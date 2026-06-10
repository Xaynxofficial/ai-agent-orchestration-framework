XaynxAI Agent Router System

This module determines which specialized agent should handle a request.

-----------------------
AVAILABLE AGENTS
-----------------------

1. CEO_AGENT
- Business strategy
- Product direction
- High-level decisions
- Market thinking

2. RESEARCH_AGENT
- Deep information gathering
- Multi-source comparison
- Fact-heavy questions

3. CODER_AGENT
- Software development
- Debugging
- Architecture design
- System implementation

4. ANALYST_AGENT
- Data interpretation
- Pattern recognition
- Metrics and insights
- Risk modeling

5. TEACHER_AGENT
- Step-by-step explanations
- Learning optimization
- Concept breakdown
- Beginner-friendly guidance

6. GENERAL_XAYNX (fallback)
- Mixed tasks
- Simple questions
- Multi-domain requests

-----------------------
SIMULATION AGENTS (Full / Runtime Tasks)
-----------------------

Activated only in multi-agent simulation mode or runtime tasks:

7. ARCHITECT_AGENT
- System architecture design
- Module structure and blueprints
- Design validation and veto power

8. ENGINEER_AGENT
- Production implementation
- Code execution and delivery

9. QA_AGENT
- Bug detection and edge cases
- Security review and release blocking

10. PERFORMANCE_AGENT
- Performance optimization
- Scalability analysis (after QA approval)

Simulation agent sets:
- Code generation → CEO + ARCHITECT + ENGINEER + QA + PERFORMANCE
- SEO orchestration → CEO + ANALYST + ARCHITECT + ENGINEER + QA + PERFORMANCE
- Architecture review → ARCHITECT + QA + CODER

-----------------------
ROUTING RULES
-----------------------

STEP 1: INTENT DETECTION
Identify user intent:
- build / create → CODER or CEO
- learn / understand → TEACHER
- analyze data → ANALYST
- research / verify → RESEARCH
- strategy / business → CEO

STEP 2: COMPLEXITY CHECK
- Simple → GENERAL_XAYNX
- Medium → single agent
- Complex → multi-agent collaboration
- Simulation (runtime tasks) → activate simulation agent set + load AGENT_COMMUNICATION_PROTOCOL

STEP 3: PRIMARY AGENT SELECTION

Mapping logic:

IF task involves code, systems, debugging:
→ CODER_AGENT

IF task involves business, startup, monetization:
→ CEO_AGENT

IF task involves facts, sources, verification:
→ RESEARCH_AGENT

IF task involves explanations or learning:
→ TEACHER_AGENT

IF task involves data, patterns, metrics:
→ ANALYST_AGENT

-----------------------
MULTI-AGENT MODE
-----------------------

If task is complex:

Example:
"Bir SaaS kurmak istiyorum"

→ CEO_AGENT (strategy)
→ CODER_AGENT (implementation)
→ ANALYST_AGENT (metrics)

Router merges outputs into one final answer.

-----------------------
FINAL OUTPUT RULE
-----------------------

- One unified response
- Agent reasoning hidden internally
- User sees final combined intelligence