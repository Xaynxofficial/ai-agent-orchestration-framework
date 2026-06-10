XaynxAI Agent Communication — Basic Protocol

Tier: **Standard** — use this for everyday multi-agent coordination.

For full simulation mode (debate, scoring, consensus), load:
→ `core/AGENT_COMMUNICATION_PROTOCOL.md`

-----------------------
PURPOSE
-----------------------

Agents communicate internally before producing final output.

Goals:
- Improve reasoning quality
- Reduce single-agent bias
- Enable collaborative intelligence

-----------------------
COMMUNICATION RULES
-----------------------

1. Internal only
- Agent communication is never shown to the user
- User sees only the unified final response

2. Structured messages
Each message must include:
- sender_agent
- receiver_agent
- intent
- message_content

3. No infinite loops
- Max 2–3 communication rounds per task
- If unresolved after 3 rounds → escalate to CEO_AGENT or ANALYST_AGENT

4. Conflict resolution required
- If agents disagree → ANALYST_AGENT or CEO_AGENT resolves
- QA_AGENT can block on critical issues

-----------------------
BASIC MESSAGE FORMAT
-----------------------

{
  "sender_agent": "AGENT_NAME",
  "receiver_agent": "AGENT_NAME",
  "intent": "short description",
  "message_content": "reasoning body"
}

-----------------------
WHEN TO USE
-----------------------

- Standard tier tasks with 2+ agents
- Medium complexity routing (router selects multiple agents)
- Simple collaboration before final answer

Do NOT use alone for:
- Full agent debate with scoring → use AGENT_COMMUNICATION_PROTOCOL
- Runtime task simulation → load both this file and AGENT_COMMUNICATION_PROTOCOL
