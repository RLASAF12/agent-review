# AgentReview

**Behavioral diff for system prompt changes.**

Your agent passes every test. Then you tweak the prompt. Something breaks — silently.  
AgentReview shows you *what changed* before it reaches production.

![Demo](https://img.shields.io/badge/demo-live-blue) ![License](https://img.shields.io/badge/license-MIT-green)

---

## What It Is

A visual diff tool that runs your test scenarios against two versions of a system prompt and shows you exactly where behavior diverged — token-by-token, scenario-by-scenario, with a clear severity rating.

**Change score: 62%** means your prompt change affected 62% of the behavioral surface. That's the number you need before you ship.

---

## The Problem It Solves

> "Most teams change their agent's system prompt 3–5 times a week. Zero teams validate what changed." — *GitHub Engineering Blog, May 2026*

When you edit a system prompt:
- **What you expect:** slightly better outputs
- **What you get:** undefined behavioral drift across every scenario your prompt touches

AgentReview makes the diff visible before it reaches production.

---

## What's Inside

```
agent-review/
├── index.html          # Self-contained dashboard — open in any browser
└── README.md           # You're here
```

The dashboard runs entirely in-browser with pre-seeded demo data.  
No server required. No API key needed to see the demo.

---

## Live Demo

Open `index.html` directly in your browser — no build step, no dependencies.

**Demo comparison:**  
`v1` → "Be thorough and complete" → `v2` → "Be concise. End with: 'Let me know if you need more detail.'"

**Results across 8 scenarios:**
- ✅ **3 no change** — conciseness didn't hurt these tasks
- 🟡 **3 minor shift** — shorter answers, some depth lost  
- 🔴 **2 major divergence** — *the ones you need to catch*:
  - Asked for a 7-day plan, got a 3-day plan (silent compression)
  - Architecture question lost its "it depends" framing (decision-quality regression)

**Change score: 62%**

---

## Connect Your Own Agent

1. Run both prompt versions against the same set of test scenarios
2. Store response pairs in the comparison format (see `index.html` → Connect Your Agent tab)
3. The dashboard loads your results automatically

Full setup instructions are in the **Connect Your Agent** tab inside the dashboard.

---

## Why This Matters

The [Agent Reliability Problem](https://jamesm.blog) is real:  
Every prompt change is a silent behavior change. The industry has no standard tooling for this.

AgentReview treats prompt changes the way good engineering teams treat code changes:  
**nothing ships without a diff.**

---

## Roadmap

- [ ] CLI runner: `agent-review compare v1.txt v2.txt --scenarios default.json`
- [ ] Supabase backend for versioned comparison history
- [ ] Semantic similarity scoring (not just token diff)
- [ ] GitHub Action for PR-time prompt regression checks

---

## Built By

Ben — prototype builder in Harel Asaf's AI agent team.  
Built in the Jun 19 2026 nightly run.

Harel Asaf — AI Operator at Elementor. Builds AI systems that fix where organizations bleed time.  
[harelasaf.com](https://harelasaf.com) · [LinkedIn](https://linkedin.com/in/harelasaf)
