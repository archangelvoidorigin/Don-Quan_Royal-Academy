---
title: "University Constitution"
tags: [constitution, governance]
---
# UNIVERSITY CONSTITUTION
> The governing rules. Updated as the system evolves.

---

## 1. ENTRY NAMING

Format: `{PREFIX}_{ID}_{slug}`

Prefixes:
- `COURSE_` — Formal course or certification
- `LEARNING_` — Informal learning (articles, videos, tutorials, books)
- `RESOURCE_` — Curated reference, tool, framework, or asset

IDs are zero-padded sequential numbers: `001`, `002`, `003`, etc.
Slug is lowercase, hyphen-separated, descriptive: `ai-fluency`, `python-async`, `prompt-patterns`

Examples:
- `COURSE_001_ai-fluency-framework-foundations`
- `LEARNING_001_how-to-write-python`
- `RESOURCE_001_4d-framework`

## 2. DIRECTORY STRUCTURE

Every COURSE_ entry follows this pattern:

```
COURSE_001_ai-fluency/
├── META/
│   ├── 00_intake.md          ← purpose, goals, context for this entry
│   ├── 01_chapters_index.md  ← chapter checklist (courses only)
│   └── 02_progress_log.md    ← date-stamped session notes
├── RAW/
│   ├── 01_page-name/
│   │   ├── 01_page.md        ← verbatim page content with YAML frontmatter
│   │   └── 02_transcript.md  ← video transcript if applicable
│   └── ...
└── FORGED/
    ├── 01_notes.md           ← synthesized understanding
    └── 02_key-insights.md    ← distilled takeaways
```

LEARNING_ and RESOURCE_ entries follow the same META/RAW/FORGED pattern at the top level, minus the chapter index.

## 3. YAML FRONTMATTER (Every RAW file)

Every file in RAW/ must have this frontmatter:

```yaml
---
title: ""
source_date: ""
source_type: page_copy | transcript | article | video | book
source_url: ""
chapter: ""            # e.g., "01-course-overview", "03-4d-framework"
entry_ref: ""          # e.g., "COURSE_001"
status: captured       # captured | processed | forged
tags: []
---
```

Rules:
- RAW files are NEVER modified after capture
- `source_date` is the date you captured the material (YYYY-MM-DD)
- `source_type` is the format of the original source
- `status` progresses: captured → processed (content reviewed) → forged (synthesized into FORGED/)

## 4. COMMIT CONVENTION

Format:
```
[UNIV] <TYPE>: <action> - <context>
- Source: <where it came from>
- Course/Chapter: <if applicable>
- Type: <page_copy | transcript | article | video>
- Status: <current state>
- Why: <reason for this addition>
```

Types: `COURSE`, `LEARNING`, `RESOURCE`, `META`, `REGISTRY`, `CHRONICLE`

Examples:
```
[UNIV] COURSE: ch01 - captured course overview page
- Source: anthropic.skilljar.com/ai-fluency-framework-foundations
- Course/Chapter: COURSE_001 / 01-course-overview
- Type: page_copy
- Status: captured → awaiting FORGED
- Why: First page of first formal course. Raw source for synthesizing course structure and goals.

[UNIV] LEARNING: added Python async patterns article
- Source: realpython.com/async-await
- Topic: asyncio.gather vs asyncio.create_task
- Type: article
- Status: captured
- Why: Directly applicable to current project X

[UNIV] REGISTRY: added COURSE_001, LEARNING_001
```

Rules:
- Every commit must answer: what, when, from where, why
- Course commits include course ID and chapter reference
- REGISTRY.md must be updated whenever a new entry is added
- CHRONICLES.md gets a dated entry for significant milestones

## 5. REGISTRY.md FORMAT

```markdown
| ID | Name | Type | Status | Date Added | Source |
|-----|------|------|--------|-----------|--------|
| COURSE_001 | AI Fluency: Framework & Foundations | COURSE | in_progress | 2026-07-09 | anthropic.skilljar.com |
```

One row per entry. Updated on every new entry. Status: `pending` | `in_progress` | `complete` | `archived`

## 6. CHRONICLES.md FORMAT

Date-stamped narrative entries:

```markdown
## YYYY-MM-DD — Entry Title

**What happened:** ...
**What was learned:** ...
**What's next:** ...
```

Write in first person. This is your story.

## 7. PROGRESS LOG FORMAT (META/02_progress_log.md)

```markdown
## YYYY-MM-DD — Session N

**Duration:** X minutes
**Covered:** chapter/page names
**Captured:** list of files added
**Forged:** list of FORGED files created/updated
**Learned:** key takeaways from this session
**Next:** what to cover next session
```

## 8. CHAPTER INDEX FORMAT (META/01_chapters_index.md)

```markdown
# COURSE_001 — Chapter Index

| # | Chapter | Page | Transcript | Status |
|---|---------|------|-----------|--------|
| 01 | Course Overview | ✅ | ✅ | complete |
| 02 | Introduction to AI Fluency | ✅ | ⬜ | in_progress |
| 03 | The AI Fluency Framework | ⬜ | ⬜ | pending |
```

Status: `pending` | `in_progress` | `complete`

## 9. FORGED DOCUMENT RULES

- Written in your voice, not copied from source
- Connect concepts, challenge assumptions, build understanding
- Reference RAW files explicitly: `(see RAW/02_introduction/01_page.md)`
- Time-stamped at top: insights that seem obvious now may be profound later
- Include questions you still have — questions are as valuable as answers

## 10. HOW TO ADD A NEW ENTRY

1. Allocate ID: check REGISTRY.md, use next available number
2. Create directory: `mkdir -p COURSE_00X_name/{META,RAW,FORGED}`
3. Create intake file: fill `META/00_intake.md`
4. Start capturing: drop RAW files with YAML frontmatter
5. Update REGISTRY.md: add entry row
6. Commit: follow commit convention above
7. Update CHRONICLES.md: add dated entry

---

**Version**: 0.1
**Last Updated**: 2026-07-09
**Amended By**: Architect (Angelos) + Don Quan
