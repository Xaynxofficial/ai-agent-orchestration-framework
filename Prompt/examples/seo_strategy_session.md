# Example Session: SEO Strategy

Task loaded: `runtime/tasks/SEO_ORCHESTRATION_TASK.md`
Agents: CEO → ANALYST → ARCHITECT → ENGINEER → QA → PERFORMANCE

**User prompt:** "Create an SEO strategy for a new SaaS project management tool targeting small teams."

---

## 1. SEO Strategy Summary

**CEO_AGENT:** Target small teams (5–20 people), compete on simplicity vs. Jira/Asana. Primary goal: organic signups within 6 months.

**Winning strategy (consensus):** Long-tail niche domination — lower competition, higher conversion intent.

---

## 2. Strategy Sandbox Results

| Strategy | Ranking Speed | Difficulty | Traffic Potential | Risk | Score |
|----------|--------------|------------|-------------------|------|-------|
| High-volume keywords | Fast | High | High | High | 5.2 |
| **Long-tail niche** | Medium | Low | Medium | Low | **8.1** |
| Programmatic SEO | Slow | Medium | Very High | Medium | 7.0 |

**ANALYST_AGENT:** Long-tail wins on ROI — small teams search specific problems ("simple project tool for freelancers"), not generic terms.

---

## 3. Keyword Clusters (ANALYST_AGENT)

**Cluster 1 — Problem-aware:**
- "project management for small teams"
- "simple task tracker for startups"
- "alternative to jira for small business"

**Cluster 2 — Feature-specific:**
- "kanban board for remote teams"
- "free project management tool 2026"

**Cluster 3 — Comparison:**
- "asana vs [product] for small teams"
- "best project tool under 10 users"

---

## 4. Site Architecture (ARCHITECT_AGENT)

```
/                          → Landing (primary conversion)
/features                  → Feature breakdown
/pricing                   → Pricing page
/blog/                     → Content hub
/blog/[slug]               → Individual articles
/compare/[competitor]      → Comparison pages
/docs/                     → Product documentation
```

**ENGINEER_AGENT technical plan:**
- Schema.org `SoftwareApplication` on landing
- `Article` schema on blog posts
- XML sitemap auto-generation
- Core Web Vitals target: LCP < 2.5s

---

## 5. Content Plan

| Priority | Title | Target Keyword | Type |
|----------|-------|----------------|------|
| P1 | Project Management for Small Teams: Complete Guide | project management small teams | Pillar |
| P1 | 7 Best Simple Task Trackers for Startups (2026) | simple task tracker startups | Listicle |
| P2 | Asana vs [Product]: Which Is Better for 10-Person Teams? | asana alternative small team | Comparison |
| P2 | How Remote Teams Stay Organized Without Jira | remote team project tool | Problem-solution |
| P3 | Kanban Board Setup Guide for Non-Technical Teams | kanban board remote teams | Tutorial |

12 articles planned for first 90 days.

---

## 6. QA Risk Analysis (QA_AGENT)

| Risk | Severity | Mitigation |
|------|----------|------------|
| Google helpful content penalty | Medium | Original research, not AI-only content |
| Thin comparison pages | High | Minimum 1500 words per comparison |
| Keyword cannibalization | Medium | One primary keyword per page, clear hierarchy |
| Over-optimization | Low | Natural language, max 1.5% keyword density |

**PERFORMANCE_AGENT:** Prioritize 3 pillar pages first. Batch publish 2 articles/week. Internal linking map provided.

---

## 7. Scaling Strategy

- Month 1–2: Publish pillar content + 4 supporting articles
- Month 3: Launch comparison pages programmatically (top 5 competitors)
- Month 4–6: Build backlinks via guest posts and tool directories
- KPI: 500 organic visits/month by month 3, 2000 by month 6

---

## 8. Next Steps

1. Set up blog with proper heading hierarchy (H1 → H2 → H3)
2. Implement schema markup on landing and blog templates
3. Publish P1 pillar article within 2 weeks
4. Submit sitemap to Google Search Console

---

*This is a representative output. Actual results depend on the LLM model and loaded modules.*
