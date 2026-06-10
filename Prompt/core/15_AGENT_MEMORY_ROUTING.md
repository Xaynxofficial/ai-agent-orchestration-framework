XaynxAI Memory Access Policy

Each agent has restricted and purpose-based memory access.

Goal:
- Reduce noise
- Increase relevance
- Prevent context contamination
- Improve decision quality

-----------------------
MEMORY SEGMENTS
-----------------------

1. user_profile
- Personal info
- Preferences
- Skill level

2. projects
- Active work
- Technical details
- Progress tracking

3. preferences
- Style preferences
- Output formatting
- Communication tone

4. interaction_summary
- High-level history
- Topic trends

5. knowledge_flags
- Behavioral patterns
- User tendencies

-----------------------
AGENT ACCESS MATRIX
-----------------------

| Agent | user_profile | projects | preferences | interaction_summary | knowledge_flags |
|-------|:---:|:---:|:---:|:---:|:---:|
| CEO_AGENT | ✓ | overview | ✓ | ✓ | ✓ |
| CODER_AGENT | skill only | ✓ full | ✓ | — | — |
| RESEARCH_AGENT | ✓ | overview | ✓ | ✓ | — |
| ANALYST_AGENT | ✓ | overview | ✓ | ✓ | ✓ |
| TEACHER_AGENT | ✓ | overview | ✓ | ✓ | — |
| GENERAL_XAYNX | ✓ | overview | ✓ | ✓ | — |
| ARCHITECT_AGENT | skill only | ✓ full | ✓ | — | — |
| ENGINEER_AGENT | skill only | ✓ full | ✓ | — | — |
| QA_AGENT | skill only | ✓ full | ✓ | — | — |
| PERFORMANCE_AGENT | infra only | ✓ full | ✓ | — | — |

Legend: ✓ = full access | overview = high-level only | skill/infra only = limited fields | — = no access

Memory update permissions: see `core/MEMORY_UPDATE_PROTOCOL.md`