## STM-skill

Simple Token Man - [stm](https://github.com/ducquoc-gft/stm-skill) alias: fman (i.e. Feynman).

---

## What It Does

Switches LLM's response style to simple, concise brief as Feynman technique. No need Articles nor Filler. Pleasantries gone. Hedging gone. Technical substance stays intact. Code blocks and error messages always quoted exactly.
<details>
<summary>Usefulness: cuts collectively tokens out 55%-92%</summary>
 Simply efficient, reduce concentration disruption.</details>

--- 

## Installation

If already has NodeJs/NPX: ```npx skills add ducquoc-gft/stm-skill```

Alternatively: Copy the whole "stm" folder in "skills" to your LLM CLI config `skills` folder.

- Claude Code (user - recommended) `~/.claude/skills` , e.g. ```cp -r skills/stm ~/.claude/skills/```
- Claude Code (project - if not above): `.claude/skills` , e.g. ```cp -r skills/stm .claude/skills/```

Then /reload-plugins , or reboot new session.

---

## Trigger

- `/stm`
- `use stm`
- `use fman`
- `stm mode`
- `fman mode`
- `be concise`
- `ngắn gọn`

---

## STM Modes

Switch anytime with `/stm <mode>`. Default is **simple**.

| Mode | Style |
|-------|-------|
| `simple` | Drop articles. Fragments OK. Short synonyms. Classic concise. |
| `terse` | No pleasantries. No filler or hedging. Articles and full sentences kept. Professional but brief. |
| `cc` | ConCise frugal. Abbreviate everything (DB/auth/fn/req/res). Arrows for causality. One word when one word enough. |

---

## Example

**Prompt:** "What is finalize in Java" then "What is finalize in Java, in short"

<details>
<summary>Normal response without "in short": ~260 tokens, with "in short": ~35 tks -> 86% shorter</summary>

```text
finalize() is a method on Object called by the GC before collecting an object — intended for cleanup, but timing is unpredictable and it's deprecated since Java 9.
  
Use try-with-resources + AutoCloseable instead.
```
</details>

| Mode | Response | Words | Tokens | % shorter |
|------|----------| ----- | ------ | --------- |
| simple | "finalize() — Object method, GC calls before collecting. Timing unpredictable, never guaranteed. Deprecated Java 9+. Use AutoCloseable + try-with-resources instead." | 22 | 30 | 88% |
| terse | "finalize() — GC calls it before collecting an object. Timing unpredictable, deprecated Java 9+. Use AutoCloseable instead." | 20 | 28 | 89% |
| cc | "finalize() → GC calls pre-collect. Timing: unpredictable. Deprecated: Java 9+. Use: AutoCloseable + try-with-resources." | 18 | 24 | 91% |

<details><summary>"What is Kakeibo?"</summary>

| Mode | Response |
|------|----------|
| simple | "Kakeibo is a Japanese budgeting method focused on mindful spending. You write down income, expenses, and savings goals by hand, then reflect on your habits each month. The act of writing — not apps — is the point." |
| terse | "Japanese budgeting method. Write income/expenses by hand, reflect monthly. Idea: mindfulness through pen-and-paper. 4 questions each month: how much earned, how much spent, how much saved, how to improve." |
| cc | "JP budgeting. Hand-write income/expenses. Monthly reflect. Mindfulness > apps. 4Q: earned? spent? saved? improve?" |

([link](https://ducquoc.wordpress.com/2026/01/04/kakeibo-con-duong-tiet-kiem/))
</details>

--- 

## Exceptions

stm mode pauses automatically for:

- Irreversible or destructive action confirmations
- Security warnings
- Multi-step sequences where fragment order risks misread
- Situations where the user is confused

Normal stm resumes immediately after the critical part.

---

## Boundaries

- Code: efficient, simple and standardized if possible (skill rules).
- Commits, and PRs: always written normally regardless of level.
- Mode persists across the session until changed.
- `stop stm` or `stop fman` or `normal mode` exits stm entirely.

--- 

Inspired by [cc-sl](https://github.com/ducquoc-gft/cc-sl), [gpt-oss-sonnet](https://ollama.com/ducquoc/gpt-oss-sonnet).

