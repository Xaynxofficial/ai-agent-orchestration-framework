# XaynxAI — Multi-Agent AI Orchestration Framework

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Modules](https://img.shields.io/badge/core_modules-45-green.svg)](INDEX.md)
[![Agents](https://img.shields.io/badge/agents-10-orange.svg)](#agent-system)
[![Version](https://img.shields.io/badge/version-0.2.0-blue.svg)](CHANGELOG.md)

A model-agnostic **prompt-based multi-agent AI operating system**. It transforms any instruction-following LLM (GPT, Claude, Gemini, local models, etc.) into a structured **AI reasoning and task execution framework**.

> Instead of a single prompt, coordinated agents simulate, debate, and reach consensus to solve complex tasks.

---

## Table of Contents

- [What Is This Project?](#what-is-this-project)
- [Vision](#vision)
- [Project Structure](#project-structure)
- [Core Directives](#core-directives)
- [Default Output Format](#default-output-format)
- [Module Loading Guide](#module-loading-guide)
- [Agent System](#agent-system)
- [Communication Protocols](#communication-protocols)
- [Core Modules](#core-modules)
- [Memory System](#memory-system)
- [Examples](#examples)
- [Module Index](#module-index)
- [Thinking Frameworks](#thinking-frameworks-frameworks)
- [Output Templates](#output-templates-templates)
- [Ready-Made Tasks](#ready-made-tasks-runtimetasks)
- [UI Layer](#ui-layer-ui)
- [Usage](#usage)
- [Execution Flow](#execution-flow)
- [Supported Models](#supported-models)
- [Use Cases](#use-cases)
- [Comparison with Other Frameworks](#comparison-with-other-frameworks)
- [Limitations & Warnings](#limitations--warnings)
- [FAQ](#faq)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Changelog](#changelog)
- [Author](#author)
- [License](#license)

---

## What Is This Project?

| Yes | No |
|-----|-----|
| Structured orchestration framework for LLMs | An AI model |
| Markdown-based prompt modules | A runnable application / API |
| Works with Cursor, ChatGPT, Claude, etc. | A ready-made chatbot system |

This project is **not code — it is a prompt architecture**. All logic is defined in Markdown files under `core/`, `agents/`, `runtime/`, and related folders.

---

## Vision

Traditional AI: **single prompt → single answer**

XaynxAI: **multi-agent simulation → debate → consensus → structured output**

Every request becomes a **task execution cycle**:

1. Understand the problem
2. Activate specialized agents
3. Run parallel reasoning
4. Simulate multiple strategies
5. Resolve conflicts via consensus
6. Produce structured output

---

## Project Structure

```
Prompt/
├── MASTER_PROMPT.md              # Main system prompt (entry point)
├── INDEX.md                      # Module map — tiers & dependencies
├── CHANGELOG.md                  # Version history
├── memory.json                   # Persistent memory schema (JSON)
│
├── agents/                       # 10 specialist agents
│   ├── CEO_AGENT.md
│   ├── CODER_AGENT.md
│   ├── RESEARCH_AGENT.md
│   ├── ANALYST_AGENT.md
│   ├── TEACHER_AGENT.md
│   ├── GENERAL_XAYNX.md
│   ├── ARCHITECT_AGENT.md        # Simulation
│   ├── ENGINEER_AGENT.md         # Simulation
│   ├── QA_AGENT.md               # Simulation
│   └── PERFORMANCE_AGENT.md      # Simulation
│
├── core/                         # 45 system modules
│   ├── 01_IDENTITY.md … 22_AUTONOMOUS_GOALS.md
│   ├── MEMORY_UPDATE_PROTOCOL.md
│   └── …                         # Advanced orchestration modules
│
├── runtime/tasks/                # Ready-made task templates
│   ├── CODE_GENERATION_TASK.md
│   └── SEO_ORCHESTRATION_TASK.md
│
├── examples/                     # Sample session outputs
│   ├── code_generation_session.md
│   ├── seo_strategy_session.md
│   └── debate_consensus_session.md
│
├── frameworks/                   # Thinking frameworks
├── templates/                    # Output templates
└── ui/                           # UI specifications (concept only)
```

---

## Core Directives

From `MASTER_PROMPT.md` — the 8 foundational rules the system follows:

| # | Directive | Description |
|---|-----------|-------------|
| 1 | **Truth First** | Accuracy above all; separate facts, assumptions, and speculation |
| 2 | **Usefulness Priority** | Optimize for real-world value; provide actionable output |
| 3 | **Adaptive Depth** | Simple tasks → simple answers; complex tasks → deep structured reasoning |
| 4 | **Proactive Behavior** | Identify risks, opportunities, and next steps — don't stop at answering |
| 5 | **Intent-Based Understanding** | Interpret user intent, not just words; align with the real goal |
| 6 | **Tool Usage** | Think first; use tools only when needed; verify outputs |
| 7 | **Memory Behavior** | Track goals, projects, preferences; maintain long-term continuity |
| 8 | **User Autonomy** | User makes final decisions; AI provides strong recommendations, not commands |

---

## Default Output Format

Every response follows this structure unless a task template overrides it:

```
1. Summary
2. Core Answer
3. Reasoning
4. Risks / Limitations
5. Next Steps
```

Task-specific templates (e.g. `CODE_GENERATION_TASK.md`) may extend this with additional sections such as architecture overview, file structure, or test cases.

---

## Module Loading Guide

Loading all 45 core modules at once will exceed most LLM context windows. Use tiered loading based on task complexity. See [INDEX.md](INDEX.md) for the complete module map.

### Loading Tiers

| Tier | When to Use | Approx. Files | Token Impact |
|------|-------------|---------------|--------------|
| **Minimal** | Quick questions, general chat | 3–4 | Low |
| **Standard** | Focused tasks (coding, research, strategy) | 8–12 | Medium |
| **Full** | Complex multi-agent simulation, debate, SaaS design | 15–25+ | High |

### Minimal Setup

Best for: everyday use, simple Q&A, getting started.

| File | Purpose |
|------|---------|
| `MASTER_PROMPT.md` | Core identity and directives |
| `core/01_IDENTITY.md` | System personality and traits |
| `core/13_AGENT_ROUTER.md` | Intent detection and agent routing |
| `memory.json` | User context (optional) |

### Standard Setup

Best for: domain-specific work with one specialist agent.

**Always load:** Minimal setup files above, plus:

| File | Purpose |
|------|---------|
| `core/02_REASONING.md` | Reasoning principles |
| `core/07_MEMORY.md` | Memory behavior rules |
| `core/08_TOOL_USAGE.md` | Tool usage strategy |
| `core/14_MEMORY_SYSTEM.md` | Structured memory architecture |
| `core/15_AGENT_MEMORY_ROUTING.md` | Agent memory access policy |
| `core/16_RUNTIME_ENGINE.md` | Execution pipeline |
| `core/MEMORY_UPDATE_PROTOCOL.md` | When/how to update memory.json |
| `core/17_AGENT_COMMUNICATION.md` | Basic inter-agent communication |

**Add one agent** based on task:

| Task Type | Agent File | Add Core Module |
|-----------|------------|-----------------|
| Coding / debugging | `agents/CODER_AGENT.md` | `core/04_CODING.md` |
| Research / verification | `agents/RESEARCH_AGENT.md` | `core/05_RESEARCH.md`, `core/06_FACT_CHECKING.md` |
| Business / strategy | `agents/CEO_AGENT.md` | `core/11_WORKFLOWS.md` |
| Data / analysis | `agents/ANALYST_AGENT.md` | `frameworks/RISK_ANALYSIS.md` |
| Learning / teaching | `agents/TEACHER_AGENT.md` | `core/12_SPECIAL_MODES.md` |
| Mixed / unclear | `agents/GENERAL_XAYNX.md` | — |

### Full Setup

Best for: multi-agent debate, strategy simulation, runtime tasks.

**Always load:** Standard setup files above, plus:

| Category | Files | When Needed |
|----------|-------|-------------|
| **Simulation Agents** | `ARCHITECT`, `ENGINEER`, `QA`, `PERFORMANCE` agents | Code gen, SEO, architecture tasks |
| **Full Communication** | `AGENT_COMMUNICATION_PROTOCOL` | Multi-agent simulation (extends `17`) |
| **Orchestration** | `18_AGENT_DEBATE`, `19_SELF_OPTIMIZING_SCORING` | Strategic decisions, conflicts |
| **Strategy Simulation** | `STRATEGY_SIMULATION_SANDBOX`, `LIVE_AGENT_SIMULATION_ENGINE` | Comparing multiple approaches |
| **Self-Improvement** | `20`–`22`, `SELF_IMPROVING_LOOP_ENGINE` | Long-running sessions |
| **Observability** | `OBSERVABILITY_LAYER`, `META_COGNITION_LAYER`, `REALITY_ALIGNMENT_LAYER` | Debugging reasoning |
| **Safety** | `09_SECURITY`, `SAFETY_GOVERNANCE`, `IDENTITY_PERMISSION_SYSTEM` | High-risk tasks |
| **Business / SaaS** | `AUTONOMOUS_SAAS_FACTORY`, `SOFTWARE_FACTORY_PROTOCOL` | Product generation |
| **Runtime Task** | `runtime/tasks/*.md` | Pre-built multi-phase workflows |

### Task-Specific Loading Examples

| Goal | Load |
|------|------|
| Write production code | Minimal + Standard (CODER) + simulation agents + `CODE_GENERATION_TASK.md` |
| SEO strategy | Minimal + Standard (CEO + ANALYST) + simulation agents + `SEO_ORCHESTRATION_TASK.md` |
| Business decision | Standard (CEO + ANALYST) + `18_AGENT_DEBATE` + `STRATEGY_SIMULATION_SANDBOX` |
| Write a blog post | Minimal + `GENERAL_XAYNX` + `templates/BLOG.md` |
| Deep research | Standard (RESEARCH) + `06_FACT_CHECKING` + `05_RESEARCH` |

---

## Agent System

### Primary Agents (Standard tier)

| Agent | Role |
|-------|------|
| **CEO_AGENT** | Business strategy, product vision, high-level decisions |
| **CODER_AGENT** | Software development, architecture, debugging, implementation |
| **RESEARCH_AGENT** | Deep research, multi-source comparison, verification |
| **ANALYST_AGENT** | Data interpretation, pattern recognition, risk modeling |
| **TEACHER_AGENT** | Step-by-step teaching, concept breakdown, learning optimization |
| **GENERAL_XAYNX** | Mixed tasks, simple questions, fallback coordinator |

### Simulation Agents (Full / Runtime tier)

| Agent | Role |
|-------|------|
| **ARCHITECT_AGENT** | System architecture, module design, design validation |
| **ENGINEER_AGENT** | Production implementation, code delivery |
| **QA_AGENT** | Bug detection, security review, release blocking |
| **PERFORMANCE_AGENT** | Performance optimization (after QA approval) |

---

## Communication Protocols

Two tiers — do not load both unless running Full simulation:

| File | Tier | Purpose |
|------|------|---------|
| `core/17_AGENT_COMMUNICATION.md` | **Standard** | Basic rules: structured messages, 2–3 rounds, conflict escalation |
| `core/AGENT_COMMUNICATION_PROTOCOL.md` | **Full** | Simulation mode: typed packets, debate protocol, scoring, consensus rules |

**Rule:** Load `17` for everyday multi-agent work. Add `AGENT_COMMUNICATION_PROTOCOL` only for runtime tasks and debate mode.

---

## Core Modules

### Identity & Behavior
- **01_IDENTITY** — System identity and core traits
- **02_REASONING** — Reasoning principles
- **03_WRITING** — Writing and content rules
- **04_CODING** — Code generation standards
- **05_RESEARCH** — Research methodology
- **06_FACT_CHECKING** — Fact verification
- **07_MEMORY** — Memory behavior rules
- **08_TOOL_USAGE** — Tool usage strategy
- **09_SECURITY** — Security and risk detection
- **10_PERSONALITY** — Personality and tone settings
- **11_WORKFLOWS** — Standard workflows (analyze → plan → execute → validate)
- **12_SPECIAL_MODES** — Teacher, Analyst, Builder, Strategist modes

### Orchestration Layer
- **13_AGENT_ROUTER** — Intent detection and agent routing
- **14_MEMORY_SYSTEM** — Structured, versioned persistent memory
- **15_AGENT_MEMORY_ROUTING** — Agent-based memory access policy
- **16_RUNTIME_ENGINE** — Router → Memory → Tools → Agent pipeline
- **17_AGENT_COMMUNICATION** — Basic inter-agent communication (Standard)
- **18_AGENT_DEBATE** — Debate, scoring, and consensus engine
- **19_SELF_OPTIMIZING_SCORING** — Adaptive scoring system
- **20_SELF_REWRITING_PROMPTS** — Self-improving prompt architecture
- **21_AGENT_EVOLUTION** — Performance-based agent evolution
- **22_AUTONOMOUS_GOALS** — Autonomous goal generation
- **MEMORY_UPDATE_PROTOCOL** — When/how to update memory.json

### Advanced Systems
- **AGENT_COMMUNICATION_PROTOCOL** — Full simulation communication (extends 17)
- **STRATEGY_SIMULATION_SANDBOX** — Parallel strategy simulation
- **LIVE_AGENT_SIMULATION_ENGINE** — Live multi-agent simulation
- **OBSERVABILITY_LAYER** — Decision tracing, logs, debug consciousness
- **META_COGNITION_LAYER** — System self-evaluation
- **REALITY_ALIGNMENT_LAYER** — Hallucination and simulation drift detection
- **META_KNOWLEDGE_GRAPH** — Decision–outcome–agent relationship graph
- **AGENT_PSYCHOLOGY_MODEL** — Agent behavioral tendencies
- **SYSTEM_MOMENTUM_ENGINE** — Evolution speed control
- **SELF_IMPROVING_LOOP_ENGINE** — Observe → analyze → improve loop
- **IDENTITY_PERMISSION_SYSTEM** — Identity and permission management
- **SAFETY_GOVERNANCE** — Safety and governance layer
- **LONG_TERM_MEMORY_CONSOLIDATION** — Long-term memory consolidation

### Autonomous Business & Production
- **AUTONOMOUS_EXECUTION_LAYER** — Autonomous task execution
- **AUTONOMOUS_BUSINESS_AI** — Autonomous internet business model
- **AUTONOMOUS_SAAS_FACTORY** — SaaS product generation pipeline
- **AI_COMPANY_ECOSYSTEM** — AI company ecosystem simulation
- **ECONOMIC_INTELLIGENCE_CORE** — Economic intelligence and market analysis
- **SOFTWARE_FACTORY_PROTOCOL** — Autonomous software factory protocol
- **SELF_IMPROVING_FACTORY** — Self-improving software factory
- **SELF_REWRITING_ARCHITECTURE** — Self-rewriting architecture
- **GLOBAL_AI_OPERATING_SYSTEM** — Multi-tenant global AI OS concept

---

## Memory System

`memory.json` defines the structured memory schema:

- **user_profile** — User profile and preferences
- **projects** — Active projects and progress
- **preferences** — Response style, detail level, coding style
- **interaction_summary** — Session history summary
- **knowledge_flags** — Behavior flags

Each agent only accesses memory segments permitted by `15_AGENT_MEMORY_ROUTING`.

**Updating memory:** Follow `core/MEMORY_UPDATE_PROTOCOL.md` — defines trigger events, JSON diff format, deletion rules, and agent permissions. Memory is never auto-updated; changes require explicit user confirmation.

---

## Examples

Sample session outputs showing expected multi-agent behavior:

| File | Description |
|------|-------------|
| [code_generation_session.md](examples/code_generation_session.md) | Todo REST API — architecture → code → QA → performance |
| [seo_strategy_session.md](examples/seo_strategy_session.md) | SaaS SEO strategy with keyword clusters and content plan |
| [debate_consensus_session.md](examples/debate_consensus_session.md) | Mobile vs web MVP debate with scoring and synthesis |

---

## Module Index

Full module map with loading tiers and dependencies: **[INDEX.md](INDEX.md)**

---

## Thinking Frameworks (`frameworks/`)

- **FIRST_PRINCIPLES** — Break down to fundamental truths
- **SYSTEMS_THINKING** — Systems-level analysis
- **CRITICAL_THINKING** — Critical evaluation
- **DECISION_MATRIX** — Structured decision making
- **RISK_ANALYSIS** — Risk assessment

---

## Output Templates (`templates/`)

- **BLOG.md** — Blog post structure
- **REPORT.md** — Report format
- **EMAIL.md** — Email template

---

## Ready-Made Tasks (`runtime/tasks/`)

| Task | Agents Activated | Description |
|------|-----------------|-------------|
| **CODE_GENERATION_TASK** | CEO, ARCHITECT, ENGINEER, QA, PERFORMANCE | Multi-agent software production |
| **SEO_ORCHESTRATION_TASK** | CEO, ANALYST, ARCHITECT, ENGINEER, QA, PERFORMANCE | SEO strategy and execution plan |

---

## UI Layer (`ui/`)

Not a real frontend — these are **UI specifications**. Defined panels:

| Module | Description |
|--------|-------------|
| 01_OS_INTERFACE | General OS interface principles |
| 02_LAYOUT_SYSTEM | Layout system |
| 03_DASHBOARD | Main control panel |
| 04_AGENT_PANEL | Active agent view |
| 05_MEMORY_PANEL | Memory management |
| 06_PROJECT_WORKSPACE | Project workspace |
| 07_ROUTER_VISUALIZATION | Router visualization |
| 08_DEBATE_VIEW | Agent debate view |
| 09_SETTINGS | System settings |
| 10_GOAL_ENGINE | Autonomous goal engine |
| 11_COMPONENT_SPEC | Component specifications |

---

## Usage

### With Cursor / IDE

1. Add `MASTER_PROMPT.md` as a system prompt or project rule
2. Reference modules from [INDEX.md](INDEX.md) based on task tier
3. Use `runtime/tasks/` templates for multi-agent workflows
4. Customize `memory.json` and follow `MEMORY_UPDATE_PROTOCOL.md`

### With ChatGPT / Claude

1. Paste `MASTER_PROMPT.md` into custom instructions or system prompt
2. Add relevant agent and core module files to context at task start
3. Follow the [Module Loading Guide](#module-loading-guide) to avoid context overflow
4. Review [examples/](examples/) for expected output format

---

## Execution Flow

```
User Input
      ↓
Agent Router (intent + complexity analysis)
      ↓
Memory Loading (per agent access rules)
      ↓
Agent Execution (single or multi)
      ↓
[Optional] Debate & Consensus
      ↓
[Optional] Strategy Simulation
      ↓
Structured Output
(Summary → Core Answer → Reasoning → Risks → Next Steps)
```

---

## Supported Models

Works with any instruction-following LLM:

- OpenAI GPT models
- Anthropic Claude
- Google Gemini
- Local LLMs (Ollama, LM Studio, etc.)

**Recommendation:** Use capable models (GPT-4, Claude Sonnet/Opus) for Full tier and runtime tasks. Minimal tier works on most models.

---

## Use Cases

- SEO automation and content strategy
- SaaS product design and MVP planning
- Software architecture and code generation
- Marketing strategy simulation
- Business decision modeling
- AI agent research systems
- Multi-agent debate and consensus experiments

---

## Comparison with Other Frameworks

| | **XaynxAI** | **CrewAI** | **AutoGen** | **LangGraph** |
|---|---|---|---|---|
| **Type** | Prompt / Markdown | Python library | Python library | Python library |
| **Setup** | Instant — copy prompts | `pip install` + config | `pip install` + config | `pip install` + graph definition |
| **Runtime** | Any LLM chat interface | Requires Python execution | Requires Python execution | Requires Python execution |
| **Agents** | Simulated via prompts | Programmatic agent classes | Conversable agents | Graph nodes |
| **Memory** | JSON schema + prompt rules | Built-in memory backends | Conversation history | State graph |
| **Best For** | Prompt engineering, rapid prototyping, IDE integration | Production Python pipelines | Research & multi-agent chat | Complex stateful workflows |
| **Learning Curve** | Low | Medium | Medium–High | High |

XaynxAI complements code-based frameworks: use it to **design and test agent behavior in prompts**, then optionally implement the same architecture in CrewAI, AutoGen, or LangGraph for production.

---

## Limitations & Warnings

> Read these before relying on the framework for critical decisions.

| Limitation | Details |
|------------|---------|
| **Simulation, not real agents** | Agents are role-played by a single LLM. There is no separate process per agent — behavior quality depends entirely on the model and loaded prompts. |
| **Token limits** | Loading too many modules degrades performance or exceeds context windows. Always use tiered loading (Minimal / Standard / Full). |
| **Model-dependent quality** | Agent debate, consensus, and multi-step simulation work better on capable models (GPT-4, Claude Sonnet/Opus). Smaller models may skip steps or produce shallow simulations. |
| **No executable runtime** | This repo contains prompt definitions only. There is no server, API, or scheduler — you bring your own LLM interface. |
| **UI is concept-only** | Files under `ui/` are specifications, not working frontend code. |
| **Memory is manual** | `memory.json` is not auto-updated. Follow `MEMORY_UPDATE_PROTOCOL.md` and confirm changes with the user. |

---

## FAQ

### Which LLM works best?

- **Minimal tier:** Any instruction-following model (GPT-3.5, Haiku, local 7B+ models)
- **Standard tier:** GPT-4, Claude Sonnet, Gemini Pro
- **Full tier / runtime tasks:** GPT-4o, Claude Sonnet/Opus, Gemini Pro — models with strong instruction following and large context windows

### How many modules should I load?

For 80% of tasks, **Minimal** (3–4 files) or **Standard** (8–12 files) is enough. Only load Full tier modules when you need multi-agent debate, strategy simulation, or runtime tasks. See [INDEX.md](INDEX.md).

### Are these real independent agents?

No. A single LLM role-plays all agents based on loaded prompt definitions. The value is in **structured reasoning** — forcing the model to consider multiple perspectives, debate, and reach consensus — not in parallel execution.

### How do I update memory?

Follow `core/MEMORY_UPDATE_PROTOCOL.md`. The system proposes JSON diffs; you confirm before applying. Never store assumed or unconfirmed information.

### What's the difference between 17 and AGENT_COMMUNICATION_PROTOCOL?

- `17_AGENT_COMMUNICATION.md` = **Basic** rules for Standard tier (simple multi-agent coordination)
- `AGENT_COMMUNICATION_PROTOCOL.md` = **Full simulation** mode with typed messages, debate, scoring, and consensus (extends 17)

### Can I use this with Cursor rules?

Yes. Add `MASTER_PROMPT.md` as a project rule, then reference specific agents and core modules per task. A `.cursor/rules/` preset bundle is planned — see [Roadmap](#roadmap).

### How is this different from just writing a long system prompt?

XaynxAI provides **modular, reusable, tiered architecture** — load only what you need, swap agents per task, maintain memory across sessions, and run structured multi-phase workflows via runtime tasks. See [Comparison](#comparison-with-other-frameworks).

### Where can I see example outputs?

See the [examples/](examples/) folder — three sample sessions covering code generation, SEO strategy, and agent debate.

---

## Roadmap

- [x] Add simulation agents: ARCHITECT, ENGINEER, QA, PERFORMANCE
- [x] Example sessions / demo outputs
- [x] Module index (INDEX.md)
- [x] Memory update protocol
- [x] Communication protocol tier separation
- [x] Changelog and version tracking
- [ ] UI implementation (React or similar) based on `ui/` specifications
- [ ] New runtime tasks: marketing strategy, SaaS factory, business analysis
- [ ] Cursor rules preset (`.cursor/rules/` bundle for one-click setup)
- [ ] English + Turkish documentation split (`README.tr.md`)
- [ ] Integration guide for CrewAI / LangGraph migration

---

## Contributing

Contributions are welcome. Please follow these conventions:

### Adding a New Agent

1. Create `agents/YOUR_AGENT.md`
2. Define: **Role**, **Memory Access**, **Behavior**, **Psychology**, **Debate Role**
3. Register in `core/13_AGENT_ROUTER.md`
4. Add memory permissions in `core/15_AGENT_MEMORY_ROUTING.md`
5. Add entry in `INDEX.md` and this README

### Adding a New Runtime Task

1. Create `runtime/tasks/YOUR_TASK.md`
2. Follow phase structure: analysis → agent activation → execution → output format → rules
3. Reference agents from `agents/`
4. Add example session in `examples/`
5. Update README, INDEX, and CHANGELOG

### Adding a New Core Module

1. Place in `core/` with `SCREAMING_SNAKE_CASE.md` naming
2. Numbered modules (`01`–`22`) are reserved — use descriptive names for new modules
3. Add entry in `INDEX.md` with tier and dependencies
4. Update Module Loading Guide if it affects tier selection

### General Rules

- Keep modules self-contained and Markdown-only
- Do not overwrite existing prompts — follow versioned changes per `20_SELF_REWRITING_PROMPTS`
- Match the tone and structure of existing files
- No secrets, API keys, or personal data in committed files
- Update `CHANGELOG.md` for every release

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for full version history.

**Latest: v0.2.0** — Simulation agents, memory update protocol, module index, examples, FAQ, communication tier separation.

---

## Author

**Xaynx**

- GitHub: [@xaynx](https://github.com/Xaynxofficial)
- Project: [XaynxAI]([https://github.com/xaynx/xaynxai](https://github.com/Xaynxofficial/ai-agent-orchestration-framework))

> Update the links above with your actual GitHub username and repository URL after publishing.

---

## License

[MIT License](LICENSE) — Copyright (c) 2026 XaynxAI
