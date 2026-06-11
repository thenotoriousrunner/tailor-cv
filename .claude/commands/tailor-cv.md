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
