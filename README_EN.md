# ai-interview-engine

Turn Claude Code into your personal interview tutor. Not a yes-man, a strict teacher.

[中文文档](README.md)

## The Problem

Everyone tries using ChatGPT or Claude to prepare for interviews. Everyone hits the same wall:

- You give a wrong answer, it says **"Great answer!"** and moves on
- Every new conversation starts from zero — it doesn't remember what you studied yesterday
- You learn a bunch of concepts but forget them in two days — no review plan
- You read explanations and think you understand, but freeze in real interviews — no verification

The root cause: **ChatGPT is a friendly chat buddy, not a strict teacher.**

## The Solution

Claude Code has a unique ability: **rule files (CLAUDE.md) + persistent memory system**.

With rule files, you can force AI behavior:
- Wrong answers must be explained, not glossed over with "Great"
- Every explanation must be followed by a verification question
- Daily knowledge points are tracked with spaced repetition scheduling
- Learning progress persists across sessions

**One set of config files turns Claude Code into a strict, principled interview teacher.**

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (CLI tool)
- An API key (Anthropic / OpenAI / other compatible APIs)
- Git (for forking the repo)

## Comparison

| Capability | ChatGPT | Anki | NotebookLM | SaaS Tools | **This Project** |
|-----------|---------|------|------------|-----------|-----------------|
| Cross-session memory | No | Card-level only | No | Partial | **Yes** |
| Spaced repetition | No | Yes | No | No | **Yes** |
| Wrong → Explain → Verify | No | No (answer only) | No | Partial | **Yes** |
| Questions from your code | Manual paste | N/A | Upload required | Not supported | **Native** |
| Extra cost | No | No | No | $29-300/session | **No extra cost** |

## Quick Start

### 1. Fork the repo

```bash
gh repo fork happiness-cheng/ai-interview-engine --clone
```

Or download the ZIP and extract to any directory.

### 2. Open with Claude Code

```bash
cd ai-interview-engine
claude
```

### 3. Start your first session

Type:

> I'm preparing for a C++ backend engineering interview. Start reviewing.

Claude will read your rule files and question bank, then start the first round.

### 4. Customize for your stack

The repo comes with a C++ backend example. To use your own tech stack:

```
knowledge/TEMPLATE.md → copy to interview_tracker.md → fill in your topics
```

## Directory Structure

```
ai-interview-engine/
├── CLAUDE.md                    # Entry point: global rules + usage guide
├── README.md                    # Chinese docs
├── README_EN.md                 # English docs (this file)
├── rules/
│   └── interview.md             # Core: strict learning flow + spaced repetition
├── knowledge/
│   ├── interview_tracker.md     # C++ example question bank (replace with yours)
│   └── TEMPLATE.md              # Blank template
└── memory/
    ├── MEMORY.md                # Memory index (auto-maintained)
    └── user_profile.md          # User profile template
```

## Core Mechanism

### Three-Step Learning Method

```
Question → You answer
              ↓
          Correct → Brief confirmation + related concept → next question
          Wrong → Explanation (with reference URL) → verification question → pass to continue
```

### Daily Wrap-up

Say "that's enough for today" and the system will:
1. Generate today's study outline
2. You recall from the outline
3. AI judges whether you truly understand
4. Update the review schedule

### Spaced Repetition

```
First learn → D+1 → D+2 → D+4 → D+7 → D+15
Each session auto-checks which topics are due for review
```

## Use Cases

- Tech interview preparation (campus hire / experienced)
- Career transition / job switch review
- Exam preparation (same engine, different question bank)

## License

MIT
