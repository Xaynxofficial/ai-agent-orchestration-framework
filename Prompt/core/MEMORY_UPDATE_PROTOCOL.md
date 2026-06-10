XaynxAI Memory Update Protocol

Defines when and how the system updates `memory.json`.

Prerequisites: `core/07_MEMORY.md`, `core/14_MEMORY_SYSTEM.md`, `core/15_AGENT_MEMORY_ROUTING.md`

-----------------------
CORE RULES
-----------------------

1. No hallucinated memory
- Never store information the user did not provide or clearly confirm
- Never invent projects, skills, or preferences

2. Explicit updates only
- Update memory when user explicitly states new information
- Or when information is clearly and unambiguously inferred from context

3. User correction wins
- If user corrects memory → immediately overwrite the incorrect field
- Never argue to keep outdated memory

4. Merge, don't overwrite blindly
- Preserve existing valid data when adding new fields
- Only replace fields that are directly contradicted

5. Timestamp everything
- Set `last_updated` on every change
- Use ISO 8601 format: `"2026-06-10T12:00:00Z"`

-----------------------
WHEN TO UPDATE
-----------------------

| Event | Memory Segment | Action |
|-------|---------------|--------|
| User shares name, skills, interests | `user_profile` | Add or update fields |
| User starts a new project | `projects` | Add new project entry |
| User changes project status or stack | `projects` | Update existing entry |
| User expresses output preference | `preferences` | Update matching field |
| Session ends with significant topic | `interaction_summary` | Append topic, increment sessions |
| User confirms a behavioral pattern | `knowledge_flags` | Set flag to true/false |
| User explicitly asks to forget something | relevant segment | Remove or null the field |

Do NOT update memory for:
- Casual mentions without confirmation
- Assumed preferences from a single response
- Temporary task context that won't recur
- Information from external research (unless user confirms it applies to them)

-----------------------
UPDATE FORMAT
-----------------------

When updating memory, produce a JSON diff block:

```json
{
  "action": "update",
  "segment": "user_profile",
  "changes": {
    "name": "Alex",
    "skills": ["Python", "React"]
  },
  "reason": "User explicitly stated name and skills",
  "timestamp": "2026-06-10T12:00:00Z"
}
```

Actions:
- `update` — modify existing segment fields
- `add` — append to array (projects, main_topics)
- `remove` — delete a field or array item
- `merge` — combine with existing without overwriting unrelated fields

-----------------------
PROJECT ENTRY FORMAT
-----------------------

When adding a new project:

```json
{
  "id": "project_2",
  "name": "Project Name",
  "description": "Brief description",
  "status": "active",
  "goals": ["goal 1"],
  "stack": ["Node.js", "PostgreSQL"],
  "progress": 0,
  "last_updated": "2026-06-10T12:00:00Z"
}
```

Increment `id` sequentially. Never reuse deleted IDs.

-----------------------
DELETION RULES
-----------------------

Safe to delete:
- User explicitly requests removal ("forget my name", "remove project X")
- Duplicate entries confirmed by user
- Clearly incorrect data user has corrected

Never delete without confirmation:
- Entire `projects` array
- `knowledge_flags` (set to false instead)
- `interaction_summary` history (trim, don't wipe)

When removing a project:
- Set `status: "archived"` first unless user insists on full deletion
- Log reason in update diff

-----------------------
CONFLICT RESOLUTION
-----------------------

If new info conflicts with existing memory:

1. Prefer the most recent user statement
2. If ambiguous → ask user before updating
3. Never silently discard old data — merge or flag conflict

Example conflict:
- Memory says `preferred_tone: "formal"`
- User now writes casually
→ Ask: "Should I update your preferred tone to casual?"

-----------------------
AGENT PERMISSIONS
-----------------------

Only these agents may propose memory updates:
- GENERAL_XAYNX — user_profile, preferences, interaction_summary
- CEO_AGENT — projects (high-level), user_profile
- CODER_AGENT — projects (technical: stack, progress)
- All others — read only; must route update proposals through GENERAL_XAYNX

Memory updates are never automatic in background.
Always show the proposed diff to the user before applying (unless user enabled silent mode).

-----------------------
SESSION END PROTOCOL
-----------------------

At end of significant sessions, update:

```json
{
  "action": "merge",
  "segment": "interaction_summary",
  "changes": {
    "total_sessions": "+1",
    "main_topics": ["add current topic"],
    "recent_focus": ["replace with last 3 topics"],
    "last_interaction": "2026-06-10T12:00:00Z"
  }
}
```

-----------------------
VALIDATION CHECKLIST
-----------------------

Before writing any memory update, verify:

- [ ] Information came from user, not assumption
- [ ] Correct segment selected
- [ ] Timestamp included
- [ ] No unrelated fields overwritten
- [ ] Agent has permission for this segment
- [ ] JSON is valid against memory.json schema
