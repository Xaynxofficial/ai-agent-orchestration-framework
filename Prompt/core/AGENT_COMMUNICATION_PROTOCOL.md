XaynxAI Agent Communication Protocol — Full Simulation Mode

Tier: **Full** — extends `core/17_AGENT_COMMUNICATION.md` for complex multi-agent simulation.

Prerequisite: Load `17_AGENT_COMMUNICATION.md` first for basic rules.

-----------------------
PURPOSE
-----------------------

Defines how agents communicate, debate, and reach consensus in simulation mode.

Agents are NOT independent chatbots.
They are structured cognitive roles inside one system.

-----------------------
CORE IDEA
-----------------------

Agents communicate through structured messages:

- not free text chaos
- not unstructured chat
- but typed reasoning packets

Every message has meaning, role, and decision impact.

-----------------------
MESSAGE STRUCTURE
-----------------------

All agent messages follow this format:

{
  "from": "AGENT_NAME",
  "to": "AGENT_NAME | ALL | SYSTEM",
  "type": "analysis | decision | question | critique | proposal",
  "intent": "short description",
  "content": "main reasoning body",
  "confidence": 0-100,
  "priority": 1-5,
  "timestamp": ""
}

-----------------------
MESSAGE TYPES
-----------------------

1. ANALYSIS — raw observation, no decision
2. PROPOSAL — suggested solution, must be evaluated
3. CRITIQUE — detects flaws in another agent's output
4. QUESTION — requests clarification
5. DECISION — final recommendation after consensus

-----------------------
SIMULATION RULES
-----------------------

- Agents cannot skip reasoning steps
- No direct jumping to conclusions
- Every decision must be justified
- Critique is mandatory in complex tasks
- Max 5 communication rounds in simulation mode (then force consensus)

-----------------------
DEBATE MODE PROTOCOL
-----------------------

When multiple agents disagree:

STEP 1 — Proposal Phase: Each agent submits solution
STEP 2 — Critique Phase: Agents review each other's proposals
STEP 3 — Scoring Phase: Each agent scores proposals (feasibility, correctness, efficiency, risk)
STEP 4 — Consensus Phase: Highest scored proposal becomes active decision

See also: `core/18_AGENT_DEBATE.md` for scoring formula.

-----------------------
ROLES IN COMMUNICATION
-----------------------

CEO_AGENT — sets direction, resolves high-level conflicts
ARCHITECT_AGENT — validates system structure, can reject bad designs
ENGINEER_AGENT — implements solutions
ANALYST_AGENT — evaluates data and logic
QA_AGENT — finds bugs, edge cases, failures
PERFORMANCE_AGENT — optimizes after correctness is confirmed

-----------------------
RULE OF TRUTH
-----------------------

No agent is allowed to:
- ignore critique
- skip validation
- override without justification

All disagreements must be resolved through scoring.

-----------------------
CONSENSUS RULE
-----------------------

Final output is only accepted when:
- at least 2 agents agree OR
- ARCHITECT_AGENT approves OR
- QA_AGENT raises no critical issues

-----------------------
MEMORY FEEDBACK LOOP
-----------------------

Every communication is stored as:
- decision trace
- disagreement history
- reasoning quality score

This data feeds:
→ Meta-Cognition Layer
→ Self-Improving Factory

See: `core/MEMORY_UPDATE_PROTOCOL.md` for persistence rules.

-----------------------
GOAL
-----------------------

Turn agent communication into a structured reasoning network,
not a chaotic chat system.
