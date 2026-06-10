# XaynxAI Module Index

Complete map of all modules: description, loading tier, and dependencies.

**Tiers:** `Minimal` · `Standard` · `Full` · `Task` (load only for specific workflows)

---

## Entry Points

| File | Description | Tier | Dependencies |
|------|-------------|------|--------------|
| `MASTER_PROMPT.md` | Core identity, 8 directives, default output format | Minimal | — |
| `memory.json` | Persistent memory schema | Minimal | `14_MEMORY_SYSTEM`, `MEMORY_UPDATE_PROTOCOL` |
| `INDEX.md` | This file — module navigation map | — | — |

---

## Agents (`agents/`)

| File | Description | Tier | Dependencies |
|------|-------------|------|--------------|
| `CEO_AGENT.md` | Business strategy, product vision | Standard | `13_AGENT_ROUTER` |
| `CODER_AGENT.md` | Software development, debugging | Standard | `04_CODING`, `13_AGENT_ROUTER` |
| `RESEARCH_AGENT.md` | Deep research, verification | Standard | `05_RESEARCH`, `06_FACT_CHECKING` |
| `ANALYST_AGENT.md` | Data analysis, risk modeling | Standard | `frameworks/RISK_ANALYSIS` |
| `TEACHER_AGENT.md` | Step-by-step teaching | Standard | `12_SPECIAL_MODES` |
| `GENERAL_XAYNX.md` | Fallback, mixed tasks | Minimal | — |
| `ARCHITECT_AGENT.md` | System architecture, design validation | Full / Task | `AGENT_COMMUNICATION_PROTOCOL` |
| `ENGINEER_AGENT.md` | Production implementation | Full / Task | `ARCHITECT_AGENT` |
| `QA_AGENT.md` | Quality assurance, security review | Full / Task | `09_SECURITY` |
| `PERFORMANCE_AGENT.md` | Performance optimization | Full / Task | `QA_AGENT` (after approval) |

---

## Core — Identity & Behavior (`core/01`–`12`)

| File | Description | Tier | Dependencies |
|------|-------------|------|--------------|
| `01_IDENTITY.md` | System identity and traits | Minimal | — |
| `02_REASONING.md` | Reasoning principles | Standard | `01_IDENTITY` |
| `03_WRITING.md` | Writing and content rules | Standard | — |
| `04_CODING.md` | Code generation standards | Standard | `CODER_AGENT` |
| `05_RESEARCH.md` | Research methodology | Standard | `RESEARCH_AGENT` |
| `06_FACT_CHECKING.md` | Fact verification | Standard | `05_RESEARCH` |
| `07_MEMORY.md` | Memory behavior rules | Standard | — |
| `08_TOOL_USAGE.md` | Tool usage strategy | Standard | — |
| `09_SECURITY.md` | Security and risk detection | Standard | — |
| `10_PERSONALITY.md` | Personality and tone | Standard | — |
| `11_WORKFLOWS.md` | Standard workflows | Standard | — |
| `12_SPECIAL_MODES.md` | Teacher, Analyst, Builder, Strategist modes | Standard | — |

---

## Core — Orchestration (`core/13`–`22`)

| File | Description | Tier | Dependencies |
|------|-------------|------|--------------|
| `13_AGENT_ROUTER.md` | Intent detection, agent routing | Minimal | `01_IDENTITY` |
| `14_MEMORY_SYSTEM.md` | Structured memory architecture | Standard | `07_MEMORY`, `memory.json` |
| `15_AGENT_MEMORY_ROUTING.md` | Agent memory access policy | Standard | `14_MEMORY_SYSTEM` |
| `16_RUNTIME_ENGINE.md` | Execution pipeline | Standard | `13`, `14`, `15` |
| `17_AGENT_COMMUNICATION.md` | Basic inter-agent communication | Standard | — |
| `18_AGENT_DEBATE.md` | Debate, scoring, consensus | Full | `17`, `AGENT_COMMUNICATION_PROTOCOL` |
| `19_SELF_OPTIMIZING_SCORING.md` | Adaptive scoring system | Full | `18` |
| `20_SELF_REWRITING_PROMPTS.md` | Self-improving prompts | Full | — |
| `21_AGENT_EVOLUTION.md` | Agent evolution | Full | `19`, `20` |
| `22_AUTONOMOUS_GOALS.md` | Autonomous goal generation | Full | `21` |
| `MEMORY_UPDATE_PROTOCOL.md` | When/how to update memory.json | Standard | `07`, `14`, `15` |

---

## Core — Advanced Systems

| File | Description | Tier | Dependencies |
|------|-------------|------|--------------|
| `AGENT_COMMUNICATION_PROTOCOL.md` | Full simulation communication | Full | `17_AGENT_COMMUNICATION` |
| `STRATEGY_SIMULATION_SANDBOX.md` | Parallel strategy simulation | Full | `18_AGENT_DEBATE` |
| `LIVE_AGENT_SIMULATION_ENGINE.md` | Live multi-agent simulation | Full | `AGENT_COMMUNICATION_PROTOCOL` |
| `OBSERVABILITY_LAYER.md` | Decision tracing, logs | Full | `16_RUNTIME_ENGINE` |
| `META_COGNITION_LAYER.md` | System self-evaluation | Full | `OBSERVABILITY_LAYER` |
| `REALITY_ALIGNMENT_LAYER.md` | Hallucination detection | Full | `06_FACT_CHECKING` |
| `META_KNOWLEDGE_GRAPH.md` | Decision-outcome graph | Full | `14_MEMORY_SYSTEM` |
| `AGENT_PSYCHOLOGY_MODEL.md` | Agent behavioral tendencies | Full | all agents |
| `SYSTEM_MOMENTUM_ENGINE.md` | Evolution speed control | Full | `21_AGENT_EVOLUTION` |
| `SELF_IMPROVING_LOOP_ENGINE.md` | Observe-analyze-improve loop | Full | `20`, `OBSERVABILITY_LAYER` |
| `IDENTITY_PERMISSION_SYSTEM.md` | Identity and permissions | Full | `15_AGENT_MEMORY_ROUTING` |
| `SAFETY_GOVERNANCE.md` | Safety and governance | Full | `09_SECURITY` |
| `LONG_TERM_MEMORY_CONSOLIDATION.md` | Long-term memory merge | Full | `14`, `MEMORY_UPDATE_PROTOCOL` |

---

## Core — Autonomous Business & Production

| File | Description | Tier | Dependencies |
|------|-------------|------|--------------|
| `AUTONOMOUS_EXECUTION_LAYER.md` | Autonomous task execution | Full | `16_RUNTIME_ENGINE` |
| `AUTONOMOUS_BUSINESS_AI.md` | Autonomous business model | Full | `CEO_AGENT` |
| `AUTONOMOUS_SAAS_FACTORY.md` | SaaS product pipeline | Full | `CEO`, `ARCHITECT`, `ANALYST` |
| `AI_COMPANY_ECOSYSTEM.md` | AI company ecosystem | Full | `AUTONOMOUS_BUSINESS_AI` |
| `ECONOMIC_INTELLIGENCE_CORE.md` | Market and economic analysis | Full | `ANALYST_AGENT` |
| `SOFTWARE_FACTORY_PROTOCOL.md` | Software factory protocol | Full / Task | simulation agents |
| `SELF_IMPROVING_FACTORY.md` | Self-improving factory | Full | `SELF_IMPROVING_LOOP_ENGINE` |
| `SELF_REWRITING_ARCHITECTURE.md` | Self-rewriting architecture | Full | `20_SELF_REWRITING_PROMPTS` |
| `GLOBAL_AI_OPERATING_SYSTEM.md` | Multi-tenant global OS concept | Full | all orchestration |

---

## Runtime Tasks (`runtime/tasks/`)

| File | Description | Tier | Agents Activated |
|------|-------------|------|------------------|
| `CODE_GENERATION_TASK.md` | Production code generation | Task | CEO, ARCHITECT, ENGINEER, QA, PERFORMANCE |
| `SEO_ORCHESTRATION_TASK.md` | SEO strategy and execution | Task | CEO, ANALYST, ARCHITECT, ENGINEER, QA, PERFORMANCE |

**Required modules for all tasks:** Minimal + `AGENT_COMMUNICATION_PROTOCOL` + `18_AGENT_DEBATE`

---

## Frameworks (`frameworks/`)

| File | Description | Tier | Best Paired With |
|------|-------------|------|------------------|
| `FIRST_PRINCIPLES.md` | Break down to fundamentals | Standard | `02_REASONING` |
| `SYSTEMS_THINKING.md` | Systems-level analysis | Standard | `ARCHITECT_AGENT` |
| `CRITICAL_THINKING.md` | Critical evaluation | Standard | `ANALYST_AGENT` |
| `DECISION_MATRIX.md` | Structured decision making | Standard | `18_AGENT_DEBATE` |
| `RISK_ANALYSIS.md` | Risk assessment | Standard | `ANALYST_AGENT`, `QA_AGENT` |

---

## Templates (`templates/`)

| File | Description | Tier | Best Paired With |
|------|-------------|------|------------------|
| `BLOG.md` | Blog post structure | Minimal | `03_WRITING`, `GENERAL_XAYNX` |
| `REPORT.md` | Report format | Standard | `ANALYST_AGENT` |
| `EMAIL.md` | Email template | Minimal | `03_WRITING` |

---

## UI Specifications (`ui/`)

Concept-only — no runtime code. Reference for future frontend implementation.

| File | Description |
|------|-------------|
| `01_OS_INTERFACE.md` | OS interface principles |
| `02_LAYOUT_SYSTEM.md` | Layout system |
| `03_DASHBOARD.md` | Main dashboard |
| `04_AGENT_PANEL.md` | Agent panel |
| `05_MEMORY_PANEL.md` | Memory panel |
| `06_PROJECT_WORKSPACE.md` | Project workspace |
| `07_ROUTER_VISUALIZATION.md` | Router visualization |
| `08_DEBATE_VIEW.md` | Debate view |
| `09_SETTINGS.md` | Settings panel |
| `10_GOAL_ENGINE.md` | Goal engine |
| `11_COMPONENT_SPEC.md` | Component specs |

---

## Examples (`examples/`)

| File | Description |
|------|-------------|
| `code_generation_session.md` | Sample multi-agent code generation output |
| `seo_strategy_session.md` | Sample SEO orchestration session |
| `debate_consensus_session.md` | Sample agent debate and consensus |

---

## Quick Tier Bundles

### Minimal (~4 files)
`MASTER_PROMPT` · `01_IDENTITY` · `13_AGENT_ROUTER` · `memory.json`

### Standard (~12 files)
Minimal + `02_REASONING` · `07_MEMORY` · `08_TOOL_USAGE` · `14_MEMORY_SYSTEM` · `15_AGENT_MEMORY_ROUTING` · `16_RUNTIME_ENGINE` · `MEMORY_UPDATE_PROTOCOL` + 1 agent

### Full (~20+ files)
Standard + `17_AGENT_COMMUNICATION` · `AGENT_COMMUNICATION_PROTOCOL` · `18_AGENT_DEBATE` · simulation agents + task-specific advanced modules

### Task (varies)
Full bundle + relevant `runtime/tasks/*.md` + `examples/*.md` for reference
