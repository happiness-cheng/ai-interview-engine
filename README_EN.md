# AI Interview Engine

> **Turn Claude Code into your personal interview tutor. Not a yes-man, a strict teacher who builds knowledge networks.**

[中文文档](README.md)

---

## The Problem

Everyone tries using ChatGPT or Claude to prepare for interviews. Everyone hits the same wall:

| Scenario | What you expect | What actually happens |
|----------|----------------|----------------------|
| You answer wrong | Point out the error + explain clearly | "Great answer!" then next question |
| Continue the next day | Remember what you studied yesterday | Start from zero, you have to re-explain |
| After a week of study | Know what to review | No plan, random questions |
| After reading an explanation | Be able to say it in an interview | Reading ≠ understanding ≠ being able to articulate |
| Learning many topics | Know how they connect | Island-style memorization, can not connect the dots |

**Root cause: ChatGPT is a friendly chat buddy, not a strict teacher.**

It will not correct you, track your progress, schedule reviews at the forgetting curve inflection point, or verify your understanding with variant questions after you get something wrong.

---

## The Solution: Rule Files Force AI to Be a Strict Teacher

Claude Code has a unique ability: **rule files (CLAUDE.md / SKILL.md) + persistent file system**.

Through a carefully designed set of rules, we transform Claude Code from "friendly chat buddy" into "strict teacher":

### Key Features

**1. Layered Knowledge Delivery - Not a firehose of information**

Each layer is confirmed before moving to the next. Like a good teacher who waits for you to nod before continuing.

**2. Knowledge Network - Learn one point, connect a web**

Not isolated memorization - knowledge expands outward along 6 relationship types: causation, prerequisites, implementation, comparison, application, and interview patterns.

**3. 4-Level Scoring with Error Type Distinction - Not just right/wrong**

Key distinction: **expression-type Hard does not regress**. If you understand correctly but use non-standard terminology, you will not be treated as not having learned it.

**4. No Scoring for Unlearned Content - Not penalizing you for what you have not been taught**

First encounter with a topic, you answer "I don't know" - you won't get an Again. The system switches to micro-teaching, then confirms.

**5. Delayed Variant Verification - Not re-asking the same question**

After getting something wrong, the system will not immediately re-ask the same question.

**6. Forgetting Curve Review - Review when you are about to forget**

Review angles evolve over time: core definition, reasoning & comparison, boundaries & variants, interview practice.

**7. Main/Branch Line Separated Scoring - No guilt by association**

Main and branch lines are scored and scheduled independently.

**8. Cross-Session Persistence - Continue every time, not start from zero**

---

## vs Competitors

| Capability | ChatGPT | Anki | NotebookLM | SaaS Tools | **This Project** |
|-----------|---------|------|------------|-----------|-----------------|
| Layered teaching | No | No | No | No | **Yes** |
| Knowledge network | No | No | No | No | **Yes** |
| Error type distinction | No | No | No | Partial | **Yes** |
| No scoring for unlearned | No | N/A | No | No | **Yes** |
| Variant verification | No | No | No | Partial | **Yes** |
| Cross-session memory | No | Card-level | No | Partial | **Yes** |
| Spaced repetition | No | Yes | No | No | **Yes** |
| Wrong then Explain then Verify | No | Answer only | No | Partial | **Yes** |
| Questions from your code | Manual paste | N/A | Upload required | Not supported | **Native** |
| Extra cost | No | No | No | 9-300/mo | **No** |

> This project requires Claude Code and an API key. The table compares **additional costs**, not total cost.

---

## Quick Start

### 1. Fork the repo

\
Or download the ZIP and extract to any directory.

### 2. Open with Claude Code

\
### 3. Start your first session

Type:

> I am preparing for a C++ backend engineering interview. Start reviewing.

Claude will read your rule files and question bank, then start the first round of teaching.

### 4. Customize for your stack

- **Change tech stack**: Copy \ to \, fill in your topics
- **Add projects**: Fill in M2 module with your project key design decisions
- **Adjust rules**: Edit files under \ to modify teaching style, scoring criteria, etc.

---

## Directory Structure

\
---

## Use Cases

- **Campus/experienced hire tech interviews** - Systematic coverage of high-frequency topics with forgetting curve consolidation
- **Career transition interviews** - Build knowledge networks in new domains, not just memorize answers
- **Exam preparation** - Swap the question bank, engine logic stays the same
- **Project review** - Deep-dive design decisions from code, prepare for project-related interview questions

---

## How It Works

### Teaching Flow

New knowledge: Layered delivery (intuitive, definition, mechanism, confirmation, example, drill, network)
Old knowledge: Test first (no-hint question, score, targeted feedback on weak points)
Wrong answer: Delayed variant verification (not re-asking the same question), next-day re-verification

### Scoring & Review

Scoring: Again / Hard (content-type or expression-type) / Good / Easy
Review: 1 day, 3 days, 7 days, 14 days, 30 days, 60 days
Angles: Core definition, Reasoning & comparison, Boundaries & variants, Interview practice

### Knowledge Network

Anchor (current knowledge), 6 relationship types, Distinguish learned/weak/unlearned, Expand high-value branches

---

## License

MIT
