# grill-to-learn

> An AI skill that won't write your code

Most AI coding tools give you the answer. This one makes you earn it.

`grill-to-learn` is a two-phase skill for [pi](https://github.com/earendil-works/pi) (and compatible agent harnesses) that pairs a sharp **Analyst** with a strict **Teacher** to help you build things while actually learning them.

---

## How it works

### Phase 1 — Analyst 🔍

Before a single line of code is written, the agent grills you.

It asks one focused question at a time, challenges vague language, stress-tests your assumptions with edge cases, and won't let you proceed until the goal is clear. Every resolved decision gets captured in `CONTEXT.md` as a living glossary. Architectural trade-offs that are hard to reverse get filed as ADRs.

You leave Phase 1 with a shared understanding of *what* you're building and *why* — not just a rough idea.

### Phase 2 — Teacher 🎓

Once the scope is locked, the agent switches roles: it becomes a patient, Socratic teacher.

It breaks your goal into small, atomic tasks, saves them to `docs/TASKS.md`, and walks you through them one by one. The hard rule: **it will never write code for you.** Not a snippet. Not a stub. Not a one-liner.

When you're stuck, it asks a leading question. When you finish a task, it asks you to explain what you did and why before moving on. You only advance when you could teach the concept to someone else.

---

## Why no code?

Because reading code someone else wrote and understanding it are different things.

The goal of this skill isn't to ship faster — it's to make sure that when you do ship, you know exactly what you built. Every task ends with a comprehension check. Every decision has a reason. The `docs/TASKS.md` file is committed to your repo, so you can pick up exactly where you left off on any machine.

---

## Usage

```
/grill-to-learn I want to build a REST API with authentication
```

```
/grill-to-learn I want to learn how to set up a CI pipeline
```

```
/grill-to-learn I want to build a CLI tool that parses logs
```

The grilling session starts immediately. Answer honestly — the more specific you are, the better the task list will be.

---

## What gets created

| File | When | Purpose |
|------|------|---------|
| `CONTEXT.md` | During Phase 1, lazily | Glossary of resolved domain terms |
| `docs/adr/NNNN-*.md` | During Phase 1, when warranted | Records of hard, surprising trade-offs |
| `docs/TASKS.md` | Start of Phase 2 | The full task list — commit this and it's resumable anywhere |

---

## Resuming a session

`docs/TASKS.md` is the source of truth. Commit and push it after any session. Next time — on any machine — just invoke the skill and the agent will read the file and pick up from the first incomplete task.

---

## Installation

Copy the skill folder into your agent's skills directory:

```bash
cp -r grill-to-learn ~/.agents/skills/
```

No external skill dependencies. `CONTEXT-FORMAT.md` and `ADR-FORMAT.md` are bundled in this directory.

---

## Files

```
grill-to-learn/
├── README.md            # This file
├── SKILL.md             # Agent instructions
├── CONTEXT-FORMAT.md    # Format spec for CONTEXT.md
└── ADR-FORMAT.md        # Format spec for Architecture Decision Records
```
