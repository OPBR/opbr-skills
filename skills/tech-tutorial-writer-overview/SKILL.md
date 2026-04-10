# Tech Tutorial Writer — Skill Overview

This skill is a structured writing system for producing **high-quality, publish-ready technical tutorials**. Every article it generates is designed to be dropped directly into a blog, developer community, or newsletter with minimal editing.

---

## Core Purpose

The skill generates technical tutorials that guide readers through a **three-tier learning progression**:

| Tier | Target Reader | Goal |
|------|--------------|-------|
| 🌱 **Beginner** | Zero experience / career changers | Build mental models, run the first working demo, eliminate fear |
| 🚀 **Intermediate** | Has basics but hitting a ceiling | Understand the "why", master patterns, apply engineering best practices |
| 🏆 **Advanced** | Wants to break to the next level | Source-code-level analysis, architecture thinking, production war stories |

Before writing anything, the skill confirms which tier the article belongs to — because each tier has a completely different writing strategy.

---

## Article Structure (Required Sections)

Every tutorial follows this skeleton:

### 1. Hook
Opens with a relatable real-world pain point. The reader should think "that's exactly my problem." Then previews what they'll gain and how long it takes.

### 2. Mental Model
Uses everyday analogies to explain abstract concepts before touching any code. Supports ASCII diagrams or Mermaid charts for visualization. No jargon without an explanation.

### 3. Environment Setup
Lists exact dependency versions, provides a copy-paste initialization command, and pre-warns about common setup pitfalls.

### 4. Core Content
Depth varies by tier:
- **Beginner**: Every step has full runnable code + line-by-line breakdown + "what you see now" descriptions
- **Intermediate**: Wrong approach shown first, then correct approach (contrast format), with supporting performance data
- **Advanced**: Source code dives, architectural evolution (v1 → v2 → v3), real production incident examples

### 5. Hands-on Project
Every article must include one complete, runnable demo. Code has inline comments on every key line. Project structure is shown explicitly.

### 6. FAQ
3–5 high-frequency questions in a consistent format with code examples in the answers.

### 7. Summary + Next Steps
Bullet-point recap of what was learned, a clear "what to study next" path, and 2–3 curated resources.

---

## Code Quality Standards

All generated code must:

- Run without hidden dependencies
- Include error handling (try/catch, error boundaries, etc.)
- Follow the latest best practices for that language/framework
- Clearly flag any deprecated APIs
- Include TypeScript types for front-end tutorials

---

## Output Format

Each generated article comes with a **metadata block** followed by the full article body:

```
════════════════════════════
📌 Article Metadata
════════════════════════════
Title (WeChat version): ...
Title (Juejin version): ...
Tier: Beginner / Intermediate / Advanced
Summary (for Juejin description field): ...
Recommended Tags: tag1, tag2, tag3
Estimated Word Count: ~XXXX words
Target Platform: WeChat / Juejin / Both

════════════════════════════
📄 Full Article (Markdown)
════════════════════════════
[complete tutorial body]
```

---

## Platform Formatting Rules

The skill adapts its output style depending on the target platform:

### WeChat Official Account
- Title under 15 Chinese characters, must use a number or question to create curiosity
- First 100 characters must hook the reader (WeChat collapses the preview)
- Paragraphs capped at 5 lines, heavy use of short sentences
- Ends with an engagement prompt ("What problems have you run into? Drop a comment!")

### Juejin (Developer Community)
- Longer, keyword-rich titles for SEO
- Uses Juejin-specific Markdown features: `:::tip`, `:::warning`, `:::danger` callout blocks
- Comparison tables for alternative approaches
- 3,000–8,000 words for intermediate/advanced articles

---

## Domains Covered

The skill has pre-mapped learning progressions for:

- **Frontend**: HTML/CSS basics → component patterns & state management → micro-frontends & compiler internals
- **Backend**: REST APIs & auth → caching, queues, distributed systems → high-concurrency architecture & SRE
- **Algorithms**: Arrays/stacks/queues → dynamic programming & graph algorithms → system design & large-scale data
- **AI/ML**: Python basics & API calls → Prompt Engineering, fine-tuning, RAG → distributed training, inference optimization, MLOps

---

## What Makes This Different from Just "Write a Tutorial"

The skill is modeled on patterns from the highest-performing tutorials on freeCodeCamp, roadmap.sh, Juejin, and top WeChat tech accounts. The key principles it enforces:

| Principle | Description |
|-----------|-------------|
| **Scenario-first** | Every article starts with a problem, never a definition |
| **Progressive complexity** | Simplest case first, complexity added incrementally |
| **Immediate feedback loops** | Every step produces a visible result |
| **Error-friendly** | Common mistakes are shown explicitly, not avoided |
| **Moderate knowledge density** | Each article focuses on 1–3 core concepts, never a knowledge dump |
| **Visual aids** | Flowcharts, comparison tables, syntax-highlighted code blocks |
| **Conversational tone** | Addresses the reader as "you", like a senior dev explaining to a colleague |
