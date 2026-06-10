# Example Session: Agent Debate & Consensus

Modules loaded: `18_AGENT_DEBATE`, `AGENT_COMMUNICATION_PROTOCOL`, `STRATEGY_SIMULATION_SANDBOX`
Agents: CEO → ANALYST → ARCHITECT → QA

**User prompt:** "Should we build our MVP as a mobile app or a web app first?"

---

## Internal Debate (hidden from user in production)

### Proposal Phase

**CEO_AGENT (Proposal A — Web first):**
- Faster to ship, no app store approval
- Easier iteration based on user feedback
- Lower development cost for MVP validation

**ARCHITECT_AGENT (Proposal B — Mobile first):**
- Target users are field workers — mobile-native UX matters
- Push notifications drive retention
- Web can feel secondary for on-the-go workflows

**ANALYST_AGENT (Proposal C — PWA hybrid):**
- Progressive Web App: mobile experience + web deploy speed
- Single codebase, installable on home screen
- Compromise between speed and mobile UX

---

### Critique Phase

**QA_AGENT critiques Proposal A (Web):**
- Mobile browser UX may hurt retention for field workers
- No offline capability without PWA anyway

**ARCHITECT_AGENT critiques Proposal B (Mobile):**
- iOS + Android doubles MVP scope
- App store review adds 1–2 week delay

**CEO_AGENT critiques Proposal C (PWA):**
- PWA limitations on iOS (push notifications historically weak)
- May feel "cheap" compared to native

---

### Scoring Phase

| Proposal | Impact (×0.3) | Feasibility (×0.3) | Scalability (×0.2) | Risk (×0.2) | **Final** |
|----------|:---:|:---:|:---:|:---:|:---:|
| A — Web first | 7 | 9 | 6 | 3 | **6.9** |
| B — Mobile first | 8 | 5 | 8 | 7 | **5.8** |
| **C — PWA hybrid** | **8** | **8** | **7** | **4** | **7.4** |

*Formula: (Impact × 0.3) + (Feasibility × 0.3) + (Scalability × 0.2) − (Risk × 0.2)*

---

### Synthesis Phase

Winning idea: **PWA hybrid** — refined with best parts of others:
- From A: fast deployment, easy iteration
- From B: mobile-first UI design (responsive, touch-optimized)
- From C: single codebase, installable experience
- Fallback plan: if iOS PWA limits block retention → native iOS in v2

**QA_AGENT:** No critical issues. Flag: test offline mode early.

---

## User-Facing Output

### 1. Summary

Recommendation: Build MVP as a **Progressive Web App (PWA)** with mobile-first design. Balances speed-to-market with mobile UX needs.

### 2. Core Answer

**Go with PWA for MVP.** Ship in 4–6 weeks with one codebase. Design mobile-first, deploy as web, allow home-screen install. Revisit native mobile only if retention data shows PWA limits on iOS.

### 3. Reasoning

- Field workers need mobile UX → pure web fails retention test
- Native mobile doubles scope → too slow for MVP validation
- PWA delivers 80% of native UX at 40% of the cost
- CEO priority (fast validation) and architect priority (good UX) both satisfied

### 4. Risks / Limitations

- iOS PWA push notification limitations may affect re-engagement
- Offline sync requires explicit Service Worker implementation
- Some users expect App Store presence — may affect trust

### 5. Next Steps

1. Define 3 core MVP features (mobile-optimized)
2. Set up PWA manifest + Service Worker scaffold
3. Design touch-first UI mockups before coding
4. Define retention KPI: 7-day return rate > 30%
5. Decision gate at week 8: PWA sufficient or pivot to native?

---

*Internal debate is hidden from user. Only final synthesis is shown. See `core/18_AGENT_DEBATE.md`.*
