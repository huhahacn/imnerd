# imnerd

Turn jargon in an AI reply into **plain words plus one concrete example**.

An [Agent Skill](https://code.claude.com/docs/en/skills) (`SKILL.md` format — works with DSH, Claude Code, and Codex).

## The problem

By default an AI writes sentences like:

> The endpoint is decoupled via an asynchronous message queue, with retries and a dead-letter queue providing eventual consistency.

With imnerd installed:

> **Before**: The design isn't scalable.
>
> **After**: 100 users work today. 1,000 break it, because every new user means editing code.

The whole rule in one line: **a term may appear, but it may never appear naked.** First mention = one plain sentence + one concrete example. After that, use it freely.

## Two reader levels

imnerd picks a level and says which one it used.

| | Level 1 — plain (default) | Level 2 — absolute beginner |
|---|---|---|
| Turn it on with | nothing, it is the default | "I'm a beginner" / "I'm a primary-school student" / 小学生 / 小白 / "explain like I'm 5" |
| Terms | plain words first, term in brackets | none; unavoidable terms get an everyday analogy |
| Sentence length | ≤ 20 words | ≤ 10 words, one idea each |
| Analogy | domain-adjacent is fine | fridge, mailbox, classroom, traffic light |
| Ends with | the next concrete action | one small action, doable in 2 minutes |

Level 2 example:

> **Before**: Your session token expired, so we cleared the local cache and you need to re-authenticate.
>
> **After**: You were logged out. It happens when the "I'm still here" ticket runs out — like a library card that expires; the library still has your books, you just need a new card. Next: click "Sign in" and type your password. It takes 10 seconds.

## When it triggers

- Requests: "explain like I'm 5" / "I'm a beginner" / "plain English" / "too technical" / "give me an example" / 说人话 / 大白话 / 听不懂 / 太专业 / 什么意思 / 举个例子 / 小学生 / 小白
- Audience is not a peer: client, boss, PM, ops, new hire
- Three or more unexplained terms or acronyms in one reply
- Human-facing writing: README, proposal, status update, email, handover notes

## What's inside

| Section | Content |
|---|---|
| Two ways to use | you are writing a reply → self-check first; user pastes text → give the rewrite, no commentary |
| Two reader levels | the Level 1 / Level 2 table, plus 5 Level 2 rules |
| 3-step rewrite | circle the jargon → rebuild the sentence (noun→verb, passive→active, abstract→number) → add an example |
| Sentence templates | "Improve system availability" → "Fewer outages: 4 hours a month → 5 minutes" |
| Term bank | 20 ready-made translations: idempotent, cache stampede, circuit breaker, gradual rollout, technical debt, close the loop, SLO, P0/P1… |
| **Personal blacklist** | swap on sight: empower, leverage, granularity, align, playbook, underlying logic, retro, first/second/in conclusion, great question, hope this helps |
| 4 before/after rewrites | technical / workplace / data / Level 2 |
| 30-second self-check | acronym expanded? example present? sentence ≤20 words? **reply ≤800 characters**? length ≤1.5×? would an outsider ask "what does that mean?" |
| 800-character cap | every reply ≤800 chars — cut background, then the second example, then repetition; keep conclusion + one example + next action |
| Don't overdo it | no accuracy loss, no condescension, copy code/commands/API names verbatim, follow the user's vocabulary |
| Excuses table | blocks "the user is an engineer, no need to explain" and the other four |

## Install

DSH reads four skill roots (pick one):

```powershell
# Global: available in every project
git clone https://github.com/huhahacn/imnerd "$env:USERPROFILE\.agents\skills\imnerd"

# Current project only
git clone https://github.com/huhahacn/imnerd ".\.dsh\skills\imnerd"
```

| Tool | Skill roots |
|---|---|
| DSH | `~/.dsh/skills/`, `~/.agents/skills/`, `<project>/.dsh/skills/`, `<project>/.agents/skills/` |
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.agents/skills/` |

Or copy `SKILL.md` manually to `<skill root>\imnerd\SKILL.md`.

## Usage

It fires automatically once installed (the `description` line in `SKILL.md` is the trigger condition). To call it by hand: type `/imnerd` in DSH, or just say "rewrite this with imnerd".

You can also lift the term bank and before/after examples straight out of `SKILL.md` as a writing checklist.

## License

MIT — see [LICENSE](LICENSE). Use it, change it, ship it.
