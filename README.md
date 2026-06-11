# CV Tailoring Tool

Generates a tailored CV for a specific job posting using a master CV as source.

## Prerequisites

- Claude Code CLI installed
- `cv-master.md` in this directory (the annotated master CV)

## Usage

```
/tailor-cv <job-posting-url>
```

**Example:**
```
/tailor-cv https://boards.greenhouse.io/anthropic/jobs/12345
```

## What it does

1. Fetches and parses the job posting
2. Reads `cv-master.md` and its `AI-NOTE` tailoring annotations
3. Selects, reorders, and rewrites content to match the role
4. Writes the output to `cv-[company]-[role]-YYYYMMDD.md`
5. Reports tailoring decisions and any gaps in the conversation

## Output

A clean, production-ready Markdown CV — no AI-NOTEs, no meta-commentary. Target length is 1 page (2 max).

## Master CV annotations

The `cv-master.md` uses `[AI-NOTE: ...]` markers at three levels:

| Level | Purpose |
|---|---|
| Global (top of file) | Rules that apply to every output |
| Section-level | Selection and ordering logic per section |
| Entry-level | Which roles each entry targets; when to condense or omit |

See `ai-note-cv-guide.md` for guidance on writing and maintaining these annotations.
