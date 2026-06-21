# AI Interview Engine

> **Turn Claude Code into your long-term interview coach. Not a yes-man, not flashcards — a knowledge network builder.**

[中文文档](README.md) | [License: MIT](LICENSE)

---

## The Problem

Using ChatGPT to prepare for interviews:

- You get it wrong, it says "Great answer!" and moves on
- Next day, new conversation — it forgot everything you studied
- You learn concepts but forget them in two days — no review plan
- You read explanations and think you understand, but freeze in interviews

**Root cause: ChatGPT is a chat buddy, not a teacher.** It does not correct you, track progress, schedule reviews, or verify understanding.

---

## See the Difference

### Plain AI

```
You: What is Pimpl?
AI:  Pimpl (Pointer to Implementation) is a C++ design pattern that
     reduces compile dependencies by hiding implementation details
     behind a pointer... [wall of text with definition, code, pros/cons]
```

You nod and say "got it." Three days later, the interviewer asks "why use unique_ptr for Pimpl?" — you cannot answer.

### AI Interview Engine

```
You: What is Pimpl?

AI:  When you order food delivery, you only see the menu and prices.
     You don't need to know how many cooks are in the kitchen or
     what pots they use. Menu stays the same, kitchen can change.

     Pimpl is the same idea: expose only the interface, hide the
     implementation.

     Formal definition: Pimpl moves class implementation details
     into a separate implementation class, accessed through a pointer,
     isolating compile dependencies.

     One core mechanism: The header only sees a pointer, not the
     implementation class members, so changing implementation does
     not trigger recompilation.

     Quick check: Do you know why "not seeing members" reduces
     recompilation?
```

Three days later:

```
AI:  Last time you understood Pimpl's basic purpose, but copy semantics
     were unstable. Today we verify that first: if a Pimpl class needs
     value semantics, how should the copy constructor be written? Why
     can't you use the default?
```

**That is the difference: it remembers where you are weak and targets those areas.**

---

## Three Core Capabilities

### 1. Actually Teach You

Not a firehose of information — layered delivery:

```
Layer 1: Intuitive model (analogy, diagram, story)
  -> Confirmed you understand
Layer 2: Formal definition + core mechanism
  -> Confirmed you can articulate it
Layer 3: Why it works + minimal example
  -> Confirmed you can apply it
Layer 4: Pros/cons, interview drill, knowledge network
```

Key designs:
- **First encounter "I don't know" is not scored** — distinguishes "never learned" from "learned but forgot"
- **Analogy for understanding, formal model for correction** — your intuition is validated first, then formalized
- **One question at a time** — no information overload

### 2. Actually Judge Whether You Know It

Not just right/wrong — four-level scoring:

| Score | Meaning | What Happens Next |
|-------|---------|-------------------|
| **Again** | Core error or completely forgot | Re-teach differently -> variant verify -> next-day re-verify |
| **Hard** | Direction right but key gaps | Content-type (regress) vs expression-type (supplement terms, no regress) |
| **Good** | Core correct, logic complete | Normal progress |
| **Easy** | Stable, accurate, transferable | Can skip levels |

Key designs:
- **Wrong answers are not re-asked** — interleaved content, then variant verification
- **Main/branch lines scored independently** — getting Lambda wrong does not penalize your variant score
- **Review angles evolve with stage** — 1 day: definition, 3 days: reasoning, 7 days: boundaries, 14 days+: real scenarios

### 3. Actually Remember Where You Left Off

Progress saved in files, persists across sessions:

```
Day 1: Pimpl core mechanism -> Good
Day 3: Auto-check on restart -> copy semantics -> Hard
Day 7: Restart -> "Last time copy semantics were unstable, verify first today"
```

Key designs:
- **Knowledge network** — learning Pimpl auto-connects unique_ptr, RAII, Rule of Five
- **Spaced review** — 1 day -> 3 days -> 7 days -> 14 days -> 30 days -> 60 days
- **Tracker persistence** — every score written immediately, not batched at the end

---

## Quick Start

### Option 1: Fork the repo (recommended)

```bash
gh repo fork happiness-cheng/ai-interview-engine --clone
cd ai-interview-engine
claude
```

Then type:

> I'm preparing for a C++ backend engineering interview. Start reviewing.

### Option 2: Install as a standalone Skill

Copy `.claude/skills/interview/` to your project:

```bash
cp -r .claude/skills/interview /your/project/.claude/skills/
```

Then in your project, start Claude Code and type:

```
/interview C++ backend, campus hire
```

> **Difference**: Option 1 is a complete workspace with example question bank and tracker. Option 2 is a self-contained Skill package with full rules and examples — you just need to prepare your own tracker.

---

## Approach Differences

| Approach | What it does well | Main limitation |
|----------|-------------------|-----------------|
| Plain AI chat | Instant explanations, free-form Q&A | No progress tracking, no review schedule, may praise wrong answers |
| Anki | Spaced repetition, mature scheduling, proven algorithm | Not good at dynamic explanations or follow-up questions, manual card creation |
| NotebookLM | Document-based Q&A, multi-document linking | No review loop, no scoring system, no personal progress tracking |
| **AI Interview Engine** | Teaching, drilling, scoring, knowledge network, spaced review in one system | Requires Claude Code, needs knowledge base maintenance, not ideal for short, fragmented study sessions |

---

## Known Limitations

- **Requires Claude Code** — needs Claude Code CLI or desktop app, not compatible with plain ChatGPT web
- **Has usage costs** — Requires a Claude subscription, Anthropic Console API credits, or a supported third-party service. Billing depends on how you access Claude Code.
- **Plain text tracker** — no graphical interface, progress requires opening files
- **Single-user design** — no multi-user collaboration
- **Scoring depends on model judgment** — scoring consistency depends on Claude's understanding, may vary
- **No automated tests** — teaching flow correctness depends on rule file design, no automated regression testing yet

---

## Design Principles

1. **Layered delivery** — one layer at a time, confirmed before the next. Prevents information overload.
2. **Distinguish "don't know" from "forgot"** — first encounter "I don't know" is not scored. These require completely different handling.
3. **Distinguish understanding from expression** — correct understanding with non-standard terminology is not treated as not learned.
4. **Never re-ask the same question** — wrong answers get variant verification, not memorization.
5. **Main line not penalized by branches** — branch errors do not affect main line achievements.
6. **Review angles evolve** — as mastery deepens, review shifts from definition to reasoning to boundaries to real scenarios.

---

## License

[MIT](LICENSE)
