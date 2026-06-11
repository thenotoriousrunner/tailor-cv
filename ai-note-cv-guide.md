# AI-NOTE Strategy for LLM-Optimized Master CV

There is no defined standard for this — it is a convention you can design yourself based on how you want the LLM to use your master CV. The logical answer is clear: **you can and should have multiple `[AI-NOTE]` entries, one per section or experience**, not a single global one.

## Granularity of `[AI-NOTE]`

There are three levels at which to place them, each with a distinct purpose:

### 1. Global Notes (top of file)
General instructions on how to interpret the entire document:

```markdown
[AI-NOTE: This is a master CV. When generating tailored versions, 
remove all AI-NOTE lines. Always prioritize measurable outcomes 
over task descriptions.]
```

### 2. Section-Level Notes
Instructions on how to handle an entire section:

```markdown
## Projects
[AI-NOTE: Include max 2-3 projects per tailored CV. 
Prioritize based on stack overlap with the job posting.]

### VibeOps | 2024–present
...
```

### 3. Entry-Level Notes (per experience or item)
The most useful level — they tell the LLM which target role each entry is most relevant for:

```markdown
### DevOps Lead @ CompanyX | 2020–2023
[AI-NOTE: Highlight for: SRE, Platform Eng, Cloud Architect. 
De-emphasize for: pure Dev, Backend, Data roles.]
[AI-NOTE: If applying to a startup, emphasize autonomy and ownership; 
if enterprise, emphasize process and scale.]

- Redesigned CI/CD pipeline...
```

## Full Three-Level Schema

```
master-cv.md
│
├── [AI-NOTE: GLOBAL] ← general generation rules
│
├── ## Experience
│   ├── [AI-NOTE: SECTION] ← how to handle this section
│   │
│   ├── ### Job 1
│   │   ├── [AI-NOTE: ENTRY] ← when/how to use this entry
│   │   └── bullet points
│   │
│   └── ### Job 2
│       ├── [AI-NOTE: ENTRY]
│       └── bullet points
│
├── ## Projects
│   └── [AI-NOTE: SECTION]
│
└── ## Skills
    └── [AI-NOTE: SECTION]
```

The more granular and specific the notes, the smarter the LLM's choices during tailored CV generation — without needing to re-explain the context every time in the prompt.

---

## Instructions for Claude Code

When inserting `[AI-NOTE]` into an existing CV file, follow these rules:

1. **Add one global note** at the very top of the file (before the name/header), defining the document as a master CV and the removal rule for tailored versions.
2. **Add one section-level note** immediately after each `##` heading, describing the selection and prioritization criteria for that section's content.
3. **Add one or more entry-level notes** immediately after each `###` heading (individual job, project, or certification), specifying:
   - Which target roles this entry should be highlighted for
   - Which target roles it should be de-emphasized or omitted for
   - Any contextual instruction (startup vs enterprise, technical vs managerial role, etc.)
4. **Never place `[AI-NOTE]` inside bullet point lists** — always above the bullets, directly under the heading.
5. **Use consistent syntax**: always `[AI-NOTE: ...]` on a dedicated line, never inline within a sentence.
6. **Do not modify** any existing content — only insert notes without altering bullet points, dates, or descriptions.
