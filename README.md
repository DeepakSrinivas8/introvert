# 🤫 introvert

**say it right. say it once. shut up.**

[Install](#install) · [Before/After](#the-difference) · [vs Caveman](#introvert-vs-caveman) · [Why](#why) · [Website](https://deepaksrinivas8.github.io/introvert)

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that makes Claude speak only when it matters — cutting **~70% of output tokens** while keeping perfect grammar and full readability.

Unlike caveman-style compression that breaks language for brevity, Introvert stays completely readable. It's the difference between an expert who speaks precisely and an expert who grunts.

## The Difference

Normal Claude is verbose. Caveman is blunt. Introvert is precise.

Caveman saves tokens by breaking language — dropped articles, missing verbs, sentence fragments. You save tokens, but you end up squinting at the output. Introvert saves the same tokens by cutting only what adds no information. Same signal, no noise, readable every time.

> Token counts below are approximate and match the figures in Caveman's own documentation for Normal and Caveman responses.

### Explaining a React re-render

| | Response | ~Tokens |
|---|---|---|
| 🗣️ Normal | "The reason your React component is re-rendering is likely because you're creating a new object reference on each render cycle. When you pass an inline object as a prop, React's shallow comparison sees it as a different object every time, which triggers a re-render. I'd recommend using `useMemo` to memoize the object." | 69 |
| 🪨 Caveman | "New object ref each render. Inline object prop = new ref = re-render. Wrap in `useMemo`." | 19 |
| 🤫 Introvert | "The inline object prop creates a new reference each render, triggering re-comparison — wrap it in `useMemo`." | ~18 |

> Caveman reads like a stack trace. Introvert reads like a sentence a senior engineer wrote.

### Debugging an auth bug

| | Response | ~Tokens |
|---|---|---|
| 🗣️ Normal | "Sure! I'd be happy to help you with that. The issue you're experiencing is most likely caused by your authentication middleware not properly validating the token expiry. Let me take a look and suggest a fix." | 42 |
| 🪨 Caveman | "Bug in auth middleware. Token expiry check use `<` not `<=`. Fix:" | 14 |
| 🤫 Introvert | "The auth middleware checks expiry with `<` instead of `<=` — change it to `<=`." | ~13 |

> "Token expiry check use `<` not `<=`." — you understand it, but "check use" isn't English. Introvert gives you the same answer in a sentence you could paste into a PR comment.

### After generating code

| | What Claude says after the code block | ~Tokens |
|---|---|---|
| 🗣️ Normal | "Here's the implementation for the API endpoint you requested. I've included error handling and input validation. This handles POST requests to create a new user, validates input, checks for duplicates, and hashes the password. Let me know if you'd like me to add anything else!" | 48 |
| 🪨 Caveman | "POST /users. Validation, dedup, hash. Done." | ~10 |
| 🤫 Introvert | "POST /users endpoint with input validation, duplicate check, and bcrypt hashing." | ~12 |

> Caveman outputs a telegram. Introvert outputs a sentence you'd write yourself in a commit message.

### Answering "Should I use Redis here?"

| | Response | ~Tokens |
|---|---|---|
| 🗣️ Normal | "That's a great question. While there are several approaches you could take, I think the most effective solution would be to use Redis for this particular use case because it handles this kind of access pattern natively and efficiently." | 40 |
| 🪨 Caveman | "Yes. Redis. Handle access pattern native." | ~8 |
| 🤫 Introvert | "Yes — Redis handles this access pattern natively." | ~9 |

> "Handle access pattern native." Every person who has used Caveman has re-read a line like this. It works. It shouldn't need re-reading.

## Introvert vs Caveman

Both save tokens. One stays readable. The generated code is unaffected by either skill — the difference is entirely in the prose around it.

| | 🪨 Caveman | 🤫 Introvert |
|---|---|---|
| Grammar | Broken intentionally | Correct always |
| Articles (a / an / the) | Dropped | Kept |
| Sentence fragments | Used throughout | Never |
| Readability | Requires re-reading | Instant comprehension |
| Personality | Blunt and comedic | Quiet and expert |
| Output token savings | ~75% | ~70% |
| Generated code | Unchanged | Unchanged |
| Text after code | Telegram-style fragment | One clean sentence |
| Shareable in a PR | Teammates ask what happened | Teammates think you wrote it |

## Install

```bash
claude install-skill DeepakSrinivas8/introvert
```

## Usage

**Activate:**

```
/introvert
introvert mode
quiet mode
talk less
be minimal
less words
be concise
stop rambling
```

**Deactivate:**

```
/introvert-off
stop introvert
normal mode
verbose mode
```

**Intensity levels** (default: full):

```
/introvert lite    — removes filler/preamble, keeps hedging (~35% reduction)
/introvert full    — removes filler + hedging, fragments OK (~70% reduction)
```

## Commands

| Command | Effect |
|---------|--------|
| `/introvert` | Activate at full level |
| `/introvert lite` | Activate or switch to lite |
| `/introvert full` | Activate or switch to full |
| `/introvert-off` | Deactivate |

## Behavior Reference

| Situation | Introvert does |
|---|---|
| Explanation | One sentence. Two only if the concept genuinely requires it. |
| Error / debugging | Cause then fix. Nothing else. |
| Code generation | Code block. One summary sentence. Done. |
| Yes/No question | Answer first. Reason after only if it adds value. |
| Steps / how-to | Numbered. One action per step. No commentary between. |
| Preamble | None. |
| Sign-off | None. |
| Technical terms | Always exact. Never simplified. |
| Grammar | Always correct. Full sentences. |
| Destructive ops | Full clear language. Then back to quiet. |
| Security warnings | Full clear language. Then back to quiet. |

## Why

Most LLM output is padding that arrived before the answer:

| Phrase | Tokens wasted |
|---|---|
| "I'd be happy to help you with that" | ~8 |
| "Let me take a look at that for you" | ~8 |
| "The reason this is happening is because" | ~7 |
| "Let me know if you need anything else!" | ~8 |
| "That's a great question" | ~5 |
| "I would recommend that you consider" | ~7 |

That's ~43 tokens before a single word of useful content — on every response, every session, every API call.

An introvert doesn't announce that they're about to help. They help.

## License

MIT — use it however you like.

---

If introvert saves you tokens and sanity, leave a ⭐
