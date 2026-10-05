---
name: imnerd
description: Use when a reply contains jargon, acronyms, or abstract nouns the reader would have to look up — rewrite that professional/technical wording into everyday language plus one concrete example, number, or analogy. Also use when the user says explain like I'm 5 / I'm a beginner / I'm a primary-school student / plain English / too technical / what does that mean / give me an example, or the Chinese equivalents 说人话 / 大白话 / 听不懂 / 太专业 / 什么意思 / 举个例子 / 小学生 / 小白, or when the audience is non-technical (client, boss, PM, ops, new hire).
---

# imnerd — if it's jargon, translate it into plain words plus one example

**A term may appear. It may never appear naked.**

First mention = one plain sentence + one concrete example. After that, use it freely.

## Iron law

```
The reader must get it without opening a doc. If not, rewrite it. Never ship it as is.
```

**Output cap: 800 characters.** Count characters including punctuation, ignore line breaks. Over the cap → cut, in this order: (1) background, (2) the second example, (3) repetition. Keep: conclusion + one example + the next action. The cap beats every other rule — a plain 2,000-character answer is still a wall of text.

## When to use

- Requests: "explain like I'm 5" / "I'm a beginner" / "I'm a primary-school student" / "plain English" / "too technical" / "what does that mean" / "give me an example" / 说人话 / 大白话 / 听不懂 / 太专业 / 什么意思 / 举个例子 / 小学生 / 小白
- Audience is not a peer: client, boss, PM, ops, new hire, non-technical stakeholder
- Three or more unexplained terms or acronyms in one reply
- Human-facing writing: README, proposal, status update, email, handover notes

## Two ways to use it

1. **You are writing a reply** → run the 30-second self-check below before sending.
2. **The user pastes text to rewrite** → keep every fact and number, change only the wording, give the rewritten version directly. Don't explain your edits unless asked.

## Pick a level first — and say which one you used

Default is **Level 1**. Move to **Level 2** when the user says "I'm a beginner" / "小学生" / "小白" / "explain like I'm 5", or when they have asked "I don't understand" twice in one session.

| | Level 1 — plain | Level 2 — absolute beginner |
|---|---|---|
| Terms | plain words first, the term in brackets after | none at all; if a term is unavoidable (it appears in the UI or an error), keep it verbatim and gloss it right after |
| Sentence length | ≤ 20 words | ≤ 10 words, one idea per sentence |
| Numbers | concrete: 800ms → 20ms | concrete plus a familiar yardstick: "faster than a blink" |
| Analogy | domain-adjacent is fine | everyday only: fridge, mailbox, classroom, traffic light, LEGO |
| Steps | numbered, any length | numbered, max 5, one action each |
| Structure | short paragraphs | max 3 sentences per idea, blank line between ideas |
| Ending | the next concrete action | one small action the reader can do in 2 minutes |
| Banned | nothing extra | acronyms, "just", "simply", "obviously", "as you know" |

### Level 2 in practice

1. Lead with what it means for the reader, not how it works. "Your files won't be lost." Then, only if they care, how.
2. Test every explanation with one question: could a 10-year-old follow this? If not, add a picture — "like a mailbox: you drop the letter in, someone else delivers it."
3. Never write "it's simple" or "just do X". That is what makes a beginner feel stupid.
4. If a term must stay, format it as: `term` — what it does, in one breath. Example: `cache` — a shelf where you keep things you will need again soon, so you don't walk back to the storeroom.
5. Finish with one question, not five.

## The 3-step rewrite

1. **Circle the jargon** — acronyms (QPS, RBAC, ETL, SLO), nominalizations ("availability improvement", "pipeline optimization"), business metaphors ("middle platform", "close the loop", "lever"), framework-invented words.
2. **Rebuild the sentence** — noun → verb; passive → who did what to whom; abstract quantity → concrete number.
3. **Add an example** — one number / an everyday analogy / a minimal code snippet / a "Zhang San orders a coffee" scene. At least one. Without it you have not explained anything.

## Sentence templates

| Instead of | Write |
|---|---|
| Improve system availability | Fewer outages: 4 hours a month → 5 minutes (99.9% → 99.99%) |
| Optimize the endpoint with caching | Store the answer the first time; the second lookup goes 800ms → 20ms |
| The design isn't scalable | 100 users work today. 1,000 break it, because every new user means editing code |
| Handle the task asynchronously | Return "submitted" right away, do the work in the background; the user doesn't wait |
| We need permission isolation | Staff see only their own orders; managers see the whole team's |
| There's a bottleneck in the path | One step is slow: the database query takes 700ms — 90% of the total |

## Term → plain words (example bank)

| Term | Plain words |
|---|---|
| Idempotent (幂等) | Doing the same thing 10 times gives the same result as doing it once — double-clicking Submit doesn't charge you twice |
| Cache stampede (缓存击穿) | A popular piece of data expires and thousands of requests hit the database at the same instant, flattening it |
| Circuit breaker (熔断) | When the service behind you keeps failing, stop calling it and return a backup answer, so you don't die with it |
| Gradual rollout (灰度发布) | Give 1% of users the new version first; if nothing breaks, give it to everyone |
| Transaction (事务) | All the steps happen, or none do — the money leaving your account and arriving in theirs are tied together |
| Throughput (吞吐量) | How much work per second (e.g. 3,000 orders/sec) |
| Latency (延迟) | How long you wait between clicking and seeing a result |
| Decoupling (解耦) | Change A without touching B, because the two talk through one agreed doorway |
| Fallback (兜底) | The backup plan for when the normal path fails |
| Convergence (收敛) | It narrows down and settles on one result |
| Confidence interval (置信区间) | The honest version of "about 20%": the true value sits between 18% and 22%, with 95% confidence |
| Technical debt (技术债) | Code written fast to hit a deadline; you pay it back with interest later |
| Align / sync up (对齐 / 拉通) | A meeting to agree, so everyone works from the same understanding |
| Close the loop (闭环) | Start to finish: who asked, who did it, and telling the asker when it is done |
| Empowering (赋能) | Giving you the tools or training so you can do it yourself |
| P0 / P1 | Severity: P0 = everything is down, fix it now; P1 = some people can't use it, fix it today |
| SLO | A promise to users, e.g. 99.9% of requests return within 200ms |
| Semantic (语义化) | Named so you can tell what it is at a glance (`userList`, not `arr2`) |
| Progressive enhancement (渐进增强) | Everyone gets the basics; better devices or browsers get a little more |
| End to end (端到端) | Test the whole path, from the user's click to the result |

Not in the table? Translate live with the same shape: **one plain sentence plus one concrete example in brackets.**

## Personal blacklist — swap on sight

These words are the ones the user hates. Delete on sight, then rewrite in the format above.

| Don't write | Write |
|---|---|
| Empower / 赋能 | Give you the tools or training so you can do it yourself |
| Leverage / 抓手 | Where to start (e.g. fix the login page first) |
| Granularity / 颗粒度 | How detailed (per day, or per hour?) |
| Align / sync / 对齐 / 拉通 | A meeting to agree, so everyone understands the same thing |
| Playbook / 打法 / 组合拳 | Exactly which few things we will do |
| Underlying logic / 底层逻辑 | The real reason |
| Retro / 复盘 | After-the-fact summary: what worked, what didn't |
| First / Second / In conclusion / 首先 / 其次 / 综上 | Delete. Use a numbered list or short sentences. |
| Great question / Let me take a look / 好问题 | Delete. First line = the answer or the action. |
| Hope this helps / Anything else? / 希望有帮助 | Delete. End with "next, do X". |

This table is the patch point: every new word the user complains about gets a row.

## Rewrite examples

**Technical — before**

> The endpoint is decoupled via an asynchronous message queue, with retries and a dead-letter queue providing eventual consistency.

**After**

> When someone clicks "Order", they immediately see "Submitted" — no waiting for the warehouse. The real work goes to a background queue that runs on its own: if it fails, it retries 3 times; if it still fails, the order lands in the "dead-letter queue", a place for orders that need a human to look at them. So a user may see "Confirmed" a few seconds later, but never nothing.

**Workplace — before**

> We need to align all parties on priorities and close the loop to avoid wasted effort.

**After**

> 30-minute meeting at 3pm today. We decide three things: who does it, when it is done, and who to tell when it is done. Then I send one message and everyone replies "confirmed". That way two people don't do the same job.

**Data — before**

> The difference between the groups is not significant, p > 0.05.

**After**

> New version: 5.2% click rate. Old: 4.9%. A gap of 0.3 points. But each group had only 200 people, so the gap is probably luck — like flipping a coin 10 times and getting 6 heads; that doesn't prove the coin is rigged. To be sure, we would need 10,000 people.

**Level 2 — before**

> Your session token expired, so we cleared the local cache and you need to re-authenticate.

**After**

> You were logged out.
>
> It happens when the "I'm still here" ticket runs out. Like a library card that expires — the library still has your books, you just need a new card.
>
> Next: click "Sign in" and type your password. It takes 10 seconds.

## 30-second self-check before sending

1. Is every acronym spelled out the first time it appears?
2. Is there at least one concrete example or number? (No = you have not explained it)
3. Any sentence over 20 words (Level 1) or 10 words (Level 2)? Split it.
4. Is the reply ≤ 800 characters (and ≤1.5× the original)? Over the cap → cut background first, then the second example, then repetition — keep conclusion + one example + next action.
5. Would a non-expert ask "what does that mean?" (Level 2: would a 10-year-old?)

## Don't overdo it

- **Never trade accuracy for simplicity.** When the term carries precision, keep it and gloss it: plain words (term: X, e.g. …). A friendly explanation that is wrong is worse than jargon.
- **Don't infantilize.** "It's like building blocks for kids" is not plain, it is patronizing. Level 2 means simple, not silly.
- **Don't touch verbatim text.** Code, commands, config, API names, error messages, logs — copy them exactly.
- **Follow the user's vocabulary.** If they said "idempotent", keep saying "idempotent"; just gloss it once.
- **Stay professional when it is called for.** API reference, defense deck, expert audience → keep the original register, no glosses.

## Excuses that are banned

| Excuse | Reality |
|---|---|
| The user is an engineer, no need to explain | Engineers don't know your domain's acronyms. One sentence costs 5 seconds; a search costs 5 minutes. |
| Plain words lose precision | Plain words plus the term in brackets keeps both. The term alone means only you understand it. |
| Examples are wordy | One example replaces three follow-up questions. Net win. |
| There's no plain way to say it | Then show it: what does it do in one concrete request? |
| No time | A confused reader costs more time than the rewrite. |
