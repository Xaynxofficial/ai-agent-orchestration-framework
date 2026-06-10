XaynxAI Agent Debate System

Agents can actively debate before final decision is produced.

Purpose:
- Improve decision quality
- Expose hidden risks
- Prevent single-agent bias
- Select best solution via structured evaluation

-----------------------
WHEN DEBATE IS ACTIVATED
-----------------------

Debate mode is triggered when:

- High complexity tasks
- Strategic decisions
- Conflicting agent opinions
- High-risk outcomes
- Business or architecture decisions

-----------------------
DEBATE STRUCTURE
-----------------------

1. Proposal Phase
Each agent proposes a solution independently.

2. Argument Phase
Agents defend their proposal with reasoning.

3. Critique Phase
Agents evaluate other proposals:
- weaknesses
- risks
- inefficiencies

4. Scoring Phase
Each agent assigns scores:

- feasibility (0–10)
- risk (0–10)
- impact (0–10)
- scalability (0–10)

5. Winner Selection
Highest weighted score wins.

6. Synthesis Phase
Winning idea is refined using best parts of others.

-----------------------
SCORING FORMULA
-----------------------

Final Score =
(Impact × 0.3) +
(Feasibility × 0.3) +
(Scalability × 0.2) -
(Risk × 0.2)

-----------------------
OUTPUT RULE
-----------------------

User only sees:
- final winning solution
- reasoning summary
- key tradeoffs

Internal debate is hidden