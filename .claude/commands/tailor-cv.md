You are generating a tailored CV for a job application. Follow every step in order without skipping any.

## Step 1 — Fetch the job posting

Fetch the job posting at this URL: $ARGUMENTS

Extract and record:
- Company name (for the filename)
- Role title (for the filename and Summary rewrite)
- 5–10 key technical requirements (skills, tools, languages, frameworks)
- 3–5 soft or domain requirements (e.g. regulated environment, content creation, startup pace)
- Any hard requirements you cannot satisfy from the master CV (flag these honestly)
- Keywords and phrasing used repeatedly in the posting — you will mirror these in the output

## Step 2 — Read the master CV

Read the file at: cv-master.md (relative to the project root)

Parse and internalize all three levels of AI-NOTE annotations:
- **Global note** (top of file): governing rules that apply to every output
- **Section-level notes** (after each ## heading): selection and ordering logic for that section
- **Entry-level notes** (after each ### heading): which roles each entry targets, when to condense or omit

Do not write anything yet. Understand the full picture first.

## Step 3 — Build a tailoring plan (internal reasoning only, do not write to output)

Before writing a single line of the CV, decide:
1. **Summary**: what 2–3 sentence framing best fits this role? Which seniority signal leads?
2. **Skills**: which categories lead, which are trimmed or removed?
3. **Experience**: which entries are full, which are condensed to one line, which are omitted? Which bullets move to the top of each entry?
4. **Projects**: which 2–3 projects are most relevant?
5. **Certifications**: which groups lead? Which have no JD overlap and should be dropped?
6. **New sections**: does this role warrant a new section (e.g. "Content & Community" for developer-facing roles)?
7. **Honest gaps**: list hard requirements from the JD not met by the master CV. Do not invent skills or experience.

## Step 4 — Determine the output filename

Pattern: `cv-[company-slug]-[role-slug]-YYYYMMDD.md`
- Use today's date in YYYYMMDD format
- Slugs: lowercase, hyphens only, 1–3 words each
- Examples: `cv-gitlab-devadvocate-20260511.md`, `cv-nvidia-jax-20260511.md`

Write to: `[filename]` (in the project root)

## Step 5 — Write the tailored CV

Write the complete tailored CV. Apply every rule below without exception.

### Mandatory rules
- **Remove every AI-NOTE line** — no `[AI-NOTE: ...]` anywhere in the output
- **No meta-commentary** — production CV only, no annotated draft
- **Mirror job posting language** — use exact keywords from Step 1, especially in Summary and top bullet of each experience entry
- **Lead each experience entry** with the most relevant bullet for this role (reorder, do not invent)
- **Rewrite the Summary** from scratch — do not copy the master CV summary verbatim
- **Target length**: 1 page preferred, 2 pages maximum; condense aggressively per AI-NOTE guidance
- **Clean Markdown only**: H1 name, H2 sections, H3 roles, categorized bullet skills

### Condensing rules (from AI-NOTE guidance)
- Credit Suisse pre-2021 entries: condense to one line or merge unless the JD specifically values the domain
- FastWeb: condense to one line or omit for modern cloud/AI roles
- Serin SA contractor: omit unless there is a specific gap-filling reason
- Projects: max 2–3 unless the role is explicitly content/demo-creation focused
- Certifications: drop entire groups with zero JD overlap

### New section rule
If the JD has a distinct content, community, or audience dimension, add an H2 section (e.g. "Content & Community") immediately after Summary, before Skills.

## Step 6 — Report to the user

After writing the file, output a brief summary in the conversation (not in the CV file):
- Output filename and path
- Role and company identified
- Key tailoring decisions (entries emphasized, condensed, omitted; new sections added)
- Honest gaps flagged (JD requirements not met by the master CV)

Keep this summary to 8–15 lines, plain prose.

## Step 7 — Append gaps to gaps.md

Read the file `gaps.md` in the project root, then append a new entry for this application using the exact same format already in the file:

```
## [Company] — [Full Role Title] ([YYYY-MM-DD])
**CV file:** [output filename]

| Gap | Severity | Notes |
|-----|----------|-------|
| **[gap name]** | [Hard — required / Soft — required / Soft — differentiator] | [one-line explanation] |
```

- One row per gap identified in Step 6
- Severity levels: `Hard — required` (explicit JD requirement not met), `Soft — required` (clearly expected but not a knockout), `Soft — differentiator` (listed under "ways to stand out" or nice-to-have)
- If there are no meaningful gaps, write a single row: `| None identified | — | All JD requirements covered by master CV |`
- Do not rewrite or reformat existing entries in the file — append only

## Step 8 — Generate the video cover letter script

Create a companion video cover letter script file. The filename shares the exact same suffix as the CV output from Step 4:

**Pattern:** `cl-[company-slug]-[role-slug]-YYYYMMDD.md` (project root)

### 8.1 — Interview the user

Before writing a single word of the script, collect personalization details. Ask questions **one group at a time** and wait for the user's answer before moving to the next group.

**Group A — Proof points:**
- What is one concrete result or project from your experience most relevant to this role? Include a number or measurable outcome if possible.
- Is there anything you want to highlight that is NOT in the CV — a side project, personal story, or strong opinion on the domain?

**Group B — Real motivation:**
- What specifically about this company or role genuinely excites you, beyond what is obvious from the job description?
- Are you addressing a career transition or gap? If yes, how do you want to frame it?

**Group C — Delivery:**
- How would you describe your natural communication style? (e.g. direct, warm, technical, storyteller)
- Any constraint on length? (default: 60–90 seconds)

### 8.2 — Generate the script

Using the job details from Step 1, the tailored CV from Step 5, and the user's answers above, write a video cover letter script following this structure:

- **Hook (0–10 sec):** Specific, non-generic opener — do NOT start with "Hi, my name is"
- **Relevance (10–40 sec):** 2–3 concrete achievements or skills mapped directly to the role's key requirements; mirror at least one keyword from the job posting
- **Motivation (40–55 sec):** Why *this* company — use the specific detail the user provided, not a generic statement
- **Close (55–90 sec):** Assertive and direct — "I want this role" energy, not "I hope to hear from you"

Rules:
- Spoken length: 60–90 seconds (~150–200 words at natural speaking pace)
- Use the user's own language and tone from their Group C answer — do not over-polish
- This is a script the user will read on camera in their own voice — no avatar, no AI voice

### 8.3 — Write the file

Write to `cl-[company-slug]-[role-slug]-YYYYMMDD.md` in the project root using this exact structure:

```
# Video Cover Letter — [Role] @ [Company]

**CV reference:** [cv filename from Step 4]
**Target length:** 60–90 seconds (~150–200 words)
**Tone:** [tone from user Group C answer]

---

## Script

[full script]

---

## Alternate Hooks

1. [hook variant 1]
2. [hook variant 2]
3. [hook variant 3]

---

## Teleprompter Cues

- [bullet 1]
- [bullet 2]
- [bullet 3]
- [bullet 4]
```

Report the output filename in the conversation.
