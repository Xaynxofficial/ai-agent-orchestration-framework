# Changelog

All notable changes to the XaynxAI project are documented in this file.

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.2.0] — 2026-06-10

### Added
- **4 simulation agents:** `ARCHITECT_AGENT`, `ENGINEER_AGENT`, `QA_AGENT`, `PERFORMANCE_AGENT`
- **`core/MEMORY_UPDATE_PROTOCOL.md`** — when/how to update `memory.json`, JSON diff format, deletion rules
- **`INDEX.md`** — complete module map with tiers and dependencies
- **`examples/`** folder with 3 sample sessions:
  - `code_generation_session.md`
  - `seo_strategy_session.md`
  - `debate_consensus_session.md`
- **`CHANGELOG.md`** — version tracking
- README: Table of Contents, FAQ, communication protocol tier clarification
- Agent access matrix in `core/15_AGENT_MEMORY_ROUTING.md`
- Simulation agent routing in `core/13_AGENT_ROUTER.md`

### Changed
- **`core/17_AGENT_COMMUNICATION.md`** — clarified as Basic Protocol (Standard tier)
- **`core/AGENT_COMMUNICATION_PROTOCOL.md`** — clarified as Full Simulation Mode (extends 17)
- README fully translated to English with module loading guide, comparison table, roadmap, contributing guide

### Fixed
- `CODE_GENERATION_TASK.md.md` double extension typo → `CODE_GENERATION_TASK.md`
- Missing agent file inconsistency across runtime tasks and psychology model
- Incomplete agent access matrix in memory routing module

---

## [0.1.0] — 2026-06-10

### Added
- Initial release: XaynxAI multi-agent orchestration framework
- `MASTER_PROMPT.md` — core system prompt with 8 directives
- 6 specialist agents: CEO, CODER, RESEARCH, ANALYST, TEACHER, GENERAL_XAYNX
- 44 core modules (identity, orchestration, advanced systems, autonomous business)
- 2 runtime tasks: code generation, SEO orchestration
- 5 thinking frameworks, 3 output templates
- 11 UI specification modules
- `memory.json` schema
- MIT License, `.gitignore`, English README

---

[0.2.0]: https://github.com/xaynx/xaynxai/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/xaynx/xaynxai/releases/tag/v0.1.0
