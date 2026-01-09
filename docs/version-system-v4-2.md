# Falcon BMS TMS/DMS/CMS Guide Version System v4.2

**Latest Update:** 09 January 2026, 09:34 -03  
**Effective Date:** 09 January 2026  
**Replaces:** v4.1 (adds explicit reference to WIP-FILE-NAMING for individual preparation files and aligns repository workflow with GitHub branch protection and `guide.tex` canonical file)

---

## Repository Identification

- GitHub repository name: `carlos-nader/falcon-bms-hotas-tms-dms-cms-guide`
- Primary URL: https://github.com/carlos-nader/falcon-bms-hotas-tms-dms-cms-guide
- Default branch: `main`
- Canonical guide file: `guide.tex` (repository root)
- Versioned snapshots: `WIP/GUIDE/guide-vMAJOR.MINOR[.PATCH[.SUBPATCH]]-YYYYMMDD.tex`

---

## 0. How to Use This Document

### 0.1 Initial Question

Before any version change, answer:

- **Does the guide already have a published edition (≥ 1.0)?**
  - **No** → apply the **Pre-publication Regime (0.x.x.x)**.  
  - **Yes** → apply the **Post-publication Regime (x.x.x)**.  

### 0.2 Decision Steps

1. **Identify the type of change made in the work session:**
   - Did a **new chapter** enter the main guide content?
   - Was there a **strong restructuring** of sections or of how tables organize content?
   - Were there only **small adjustments** to text, formatting, or table cells?

2. **Go to the appropriate "When to Increment" table:**
   - If still in 0.x.x.x → use **Quick Reference (0.x.x.x — pre-publication)**.  
   - If already in ≥ 1.0 → use **Quick Reference (x.x.x — post-publication)**.  

3. **Apply the File Naming and Snapshot Workflow:**
   - Update the **version and date macros** in the guide's LaTeX preamble.
   - Save an updated **snapshot file** under `WIP/GUIDE/` with the new number and date.
   - Copy this snapshot over `guide.tex` in the repository root so both files are identical.
   - Update **PROJECT-TRACKING** with the new entry.
   - Keep the previous snapshot in the archive structure.

### 0.3 Scenario-Based Examples

- **"I finished the narrative of a new chapter, tables still incomplete."**
  - Regime: 0.x.x.x.  
  - Trend: **MINOR** goes up (new chapter in development), PATCH/SUBPATCH at 0.  

- **"I filled part of an important table in an existing chapter, changing how the reader uses that chapter."**
  - Regime: 0.x.x.x.  
  - Trend: **PATCH** (structural change inside the chapter).  

- **"I only fixed typos in two chapters, without changing structure or table logic."**
  - Regime: 0.x.x.x or x.x.x, depending on current state.  
  - Trend: **SUBPATCH** (in 0.x.x.x) or **PATCH** (in x.x.x).  

---

## 1. Header and Scope

### 1.1 Metadata

- **Title:** Falcon BMS TMS/DMS/CMS Guide Version System v4.2.  
- **Role:** defines how to name, number, update, and archive versions of the TMS/DMS/CMS guide.

- **Current project regime:**
  - While no edition ≥ 1.0 has been declared, the project is in **0.x.x.x pre-publication regime**.  
  - After the first published edition, the project will combine:
    - Historical 0.x.x.x line (frozen).  
    - Active versions in **x.x.x (≥ 1.0, post-publication)**.  

### 1.2 Purpose

- Establish a versioning system that:
  - Clearly distinguishes **internal work (0.x.x.x)** from **published editions (≥ 1.0)**.
  - Aligns **MAJOR** with the guide "edition", instead of internal phases (scaffold/tables/review).
  - Treats **tables as part of chapters**, not as independent versions.

### 1.3 Scope

- Applies to:
  - Canonical main guide source file in the repository root: `guide.tex`.
  - Versioned guide **snapshots** in `WIP/GUIDE/` following the `guide-v*.tex` pattern.
  - Derived artefacts: versioned PDFs, section files (`section-*.tex`), tracking documents (`PROJECT-TRACKING-*.md`), briefings.  
  - Individual preparation file names follow their own rules, defined in a separate `WIP-FILE-NAMING v*` file (`section-`, `table-`, `visual-`, `notes-`).

- Does not apply to other projects outside the TMS/DMS/CMS Guide unless explicitly stated.

### 1.4 Version Fields in the Guide's LaTeX

The guide contains version and date macros in the preamble, for example:

```latex
\newcommand{\docversion}{0.1.4.0}     % Document version number
\newcommand{\docbuild}{20260106}      % Build date YYYYMMDD
\newcommand{\docstartdate}{05 January 2026}
\newcommand{\docenddate}{DD MMM 2026}
\newcommand{\chapterscompletedof}{1/7}
\newcommand{\tablesfilledpct}{0\%}
\newcommand{\fulldocversion}{\docversion+\docbuild}
```

These macros are the **internal source of truth** for the document version.

On every version change:

- `\docversion` and `\docbuild` must be updated to reflect the new version and new date.  
- `\fulldocversion` and derived fields (cover page, status section, etc.) start displaying the new value.

The version number stored in these macros must always match:

- The number encoded in the **snapshot file name** under `WIP/GUIDE/`.  
- The number recorded in **PROJECT-TRACKING**.  

### 1.5 Repository Structure and GitHub Workflow

To align the version system with GitHub branch protection and readable diffs, the repository follows these rules:

- The repository root contains a **single canonical main file**: `guide.tex`.
- The directory `WIP/GUIDE/` contains the **current snapshot** and archived snapshots named with the full version pattern, for example:
  - `WIP/GUIDE/guide-v0.2.2.0-20260108.tex`.
- Editing rule:
  - All substantive editing of the guide is done in the **current snapshot** inside `WIP/GUIDE/`.
  - When a snapshot is ready (compiles and passes checks), an identical copy is saved as `guide.tex` in the repository root, overwriting the previous version.
  - `guide.tex` must not be edited directly; any change to its content must originate from a snapshot in `WIP/GUIDE/`.
- Git and GitHub treat `guide.tex` as the canonical history of the document, providing line-by-line diffs across commits. Snapshots in `WIP/GUIDE/` provide additional safety and traceability but do not replace Git history.

---

## 2. Global Naming Convention

### 2.1 Snapshot File Name Rule

Every **snapshot** of the main guide stored in `WIP/GUIDE/` must follow this pattern:

```text
guide-vMAJOR.MINOR[.PATCH[.SUBPATCH]]-YYYYMMDD.tex
```

- `MAJOR`, `MINOR`, `PATCH`, `SUBPATCH` are integers ≥ 0.  
- `YYYYMMDD` is the **build date** (year, month, day).  

The root file `guide.tex` keeps a **stable name** and is always a byte-identical copy of the latest snapshot that represents the active version.

### 2.2 Date Format

- The date always uses the format `YYYYMMDD` (for example, `20260106` for 06 January 2026).
- The build date is updated whenever:
  - A new version number is created (bump in any digit).
  - A relevant snapshot is compiled, even without content change, when the artefact is to be archived.

### 2.3 Examples

- Pre-publication (0.x.x.x regime) snapshots in `WIP/GUIDE/`:
  - `WIP/GUIDE/guide-v0.1.0.0-20260105.tex`.
  - `WIP/GUIDE/guide-v0.1.4.0-20260106.tex`.

- First published edition (≥ 1.0 regime, after promotion):
  - `WIP/GUIDE/guide-v1.0.0-2026XXXX.tex`.

- Major revision in a new edition:
  - `WIP/GUIDE/guide-v2.0.0-2026XXXX.tex`.

---

## 3. Pre-Publication Regime (0.x.x.x)

### 3.1 Semantics of Digits in 0.x.x.x

During pre-publication, the version number has four digits:

```text
0.MINOR.PATCH.SUBPATCH
```

- **MAJOR = 0**  
  - Indicates the guide is in an internal development line, still unpublished.  
  - Structure can change significantly (chapters entering, leaving, being reordered) with no stability commitment to the reader.  

- **MINOR (2nd digit)**  
  - Represents which nth chapter is being worked on in the guide (order of entry into the main file, not chapter number).
  - Examples:
    - `0.1.x.x` → 1st chapter in development (could be Chapter 1, 3, 5, etc.).
    - `0.2.x.x` → 2nd chapter in development (independent of being "Chapter 2").
    - ... up to `0.7.x.x` when the 7 planned chapters have entered.

- **PATCH (3rd digit)**  
  - Marks relevant structural changes inside the chapter(s) active under that MINOR:
    - Addition of new important sections.
    - Reorganisation of sections/subsections.
    - Introduction or reformulation of tables in ways that change how the chapter is used.

- **SUBPATCH (4th digit)**  
  - Logs smaller refinements without significant structural change:
    - Spelling and typo corrections.
    - Small wording improvements.
    - Localised tweaks in table cells, footnotes, or formatting.  

### 3.2 Increment Rules in 0.x.x.x

Only MAJOR is fixed (0); the other digits vary according to change type.

#### 3.2.1 Central Rule

- Only content that reaches the **guide snapshot in `WIP/GUIDE/` and the corresponding `guide.tex` copy in the repository root** can trigger MINOR/PATCH/SUBPATCH bumps.  
  - Work left only in other WIP files (`section-...tex`, `table-...tex`, `visual-...{svg,pdf,png,tex}`, `notes-...md`, drafts) does not change the version number until integrated into the snapshot and propagated to `guide.tex`.

#### 3.2.2 "When to Increment (Pre-Publication)" Table

| Situation | Increment | Note |
|----------|-----------|------|
| Start working on a new chapter in the main file | **MINOR** | Example: `0.1.x.x → 0.2.0.0`. |
| Add a new relevant section in an already active chapter | **PATCH** | Example: `0.1.1.0 → 0.1.2.0`. |
| Restructure chapter sections/subsections | **PATCH** | Keeps MINOR; changes internal architecture. |
| Fill/modify tables in a way that changes how the chapter is used | **PATCH** | Example: new HOTAS table that reorganises reading. |
| Fix LaTeX syntax errors that prevented compilation | **PATCH** | Structural "major bugfix". |
| Fix typos, punctuation, small wording adjustments | **SUBPATCH** | Example: `0.1.4.0 → 0.1.4.1`. |
| Adjust few table cells without changing logic/structure | **SUBPATCH** | Local refinement. |
| Only compile/save, with no content change | **Date** | Update `YYYYMMDD`, not version number. |
| Work in non-integrated WIP (`section-...tex`, `table-...tex`, `visual-...{svg,pdf,png,tex}`, `notes-...md`) | **None** | Version only goes up when content enters the snapshot and `guide.tex`. |

#### 3.2.3 Internal Phases as Metadata

- Phases like "chapter scaffolding", "table filling", "review" are treated as progress metadata, not as direct triggers for MAJOR changes in 0.x.x.x.
- These phases can show up:
  - In PROJECT-TRACKING.
  - In the guide's own status section.

### 3.3 Role of Tables in 0.x.x.x

#### 3.3.1 Tables as Part of Chapters

- The `hotastable` environment is defined as a presentation medium, not as an independent structural unit.
- TMS, DMS, and CMS tables:
  - Are always part of sections/chapters (Ch. 3, 4, 5, etc.).
  - Are indexed in the table appendix, reinforcing that they belong to main chapters.

#### 3.3.2 Tables and Version Increments

- **PATCH because of tables** when:
  - Inclusion, removal, or large reformulation of a table:
    - Changes how the reader navigates or understands the chapter.
    - Reorganises content (for example, replacing free text with a central reference table).

- **SUBPATCH because of tables** when:
  - Adjustments:
    - Fix cell descriptions, typos, or references.
    - Add/remove few rows without changing overall logic.
    - Adjust formatting, reference notes, or similar details.

### 3.4 Practical Examples (0.x.x.x)

#### 3.4.1 Pre-Publication Evolution Line

- `v0.1.0.0` — Introduction structured and included in guide (1st chapter in development).  
- `v0.1.3.0` — TMS chapter structured, with main sections defined.  
- `v0.1.4.0` — DMS chapter restructured; geometry fixes; new table layout adopted.  
- `v0.2.0.0` — 2nd chapter in development enters guide (for example, HOTAS fundamentals).  
- `v0.3.0.0` — 3rd chapter in development enters guide (for example, CMS), and so on, until:  
- `v0.7.0.0` — All 7 planned chapters have entered the guide (scaffolding complete).  

#### 3.4.2 Mini-Cases by Scenario

- **Case A — New chapter (Ch. 2) enters the guide:**
  - Situation: until now, only Introduction was included as a developed chapter.
  - Action: integrate Ch. 2 structure into the main file snapshot and propagate to `guide.tex`.
  - Version: `0.1.4.0 → 0.2.0.0`.  

- **Case B — DMS restructuring in Ch. 4:**
  - Situation: sections reordered, subsections regrouped, narrative adjusted.
  - Version: `0.1.3.0 → 0.1.4.0` (PATCH).  

- **Case C — Partial filling of TMS `hotastable` in Ch. 3:**
  - Situation: first table version that reorganises how the chapter is understood.
  - Version: PATCH within the corresponding MINOR, for example `0.1.4.0 → 0.1.5.0`.  

- **Case D — Typo fixes in Introduction and TMS:**
  - Situation: only typos and micro wording adjustments.
  - Version: `0.2.3.0 → 0.2.3.1` (SUBPATCH).  

---

## 4. Bridge to Publication (0.x.x.x → 1.0)

### 4.1 Criteria to Declare 1.0

A `0.a.b.c` version can be promoted to `1.0.0` when all criteria below are met:

- **Overall chapter structure is stable.**  
  - All chapters planned for the 1st edition exist and have basic narrative complete.
  - The chapter index reflects the structure to be "frozen" for readers.

- **Guide is practically usable.**  
  - A reader can follow the flow and use TMS/DMS/CMS based on existing text.
  - Tables may be partial, as long as this is clearly indicated (for example, labels like "In development" or explanatory notes).

- **Minimum consistency and clarity review done.**  
  - Unified terminology (mode names, commands, displays, etc.).
  - Critical references (Dash-1, Dash-34, Training Manual) checked at key points.

### 4.2 Transition Procedure

1. **Choose base 0.a.b.c.**  
   - Select, among existing 0.x.x.x versions, the one that best represents the state "ready for 1.0".
   - Confirm it meets the criteria in Section 4.1.

2. **Create version 1.0.0.**  
   - Update macros in the guide LaTeX snapshot:

   ```latex
   \newcommand{\docversion}{1.0.0}
   \newcommand{\docbuild}{YYYYMMDD}  % Date when 1st edition is frozen
   ```

   - Save the snapshot with the new name under `WIP/GUIDE/`:

   ```text
   WIP/GUIDE/guide-v1.0.0-YYYYMMDD.tex
   ```

   - Copy this snapshot over `guide.tex` in the repository root so both files are identical.

3. **Freeze the 0.x.x.x line.**  
   - Move or group all `WIP/GUIDE/guide-v0.*.tex` files into a history area, for example:

   ```text
   WIP/GUIDE/prepub/guide-v0.*.tex
   ```

   - Do not create new 0.* versions after 1.0.0 is born.
   - The 0.x.x.x line becomes pre-publication history only.

4. **Update tracking.**  
   - In PROJECT-TRACKING, record:
     - Which `0.a.b.c` version was promoted to `1.0.0`.
     - A short editorial justification for promotion (why this is the 1st edition).
     - The path/identifier of the archived PDF `guide-v1.0.0-YYYYMMDD.pdf`.

### 4.3 Cutover between Regimes

- From the build date recorded in `\docbuild` of version `1.0.0` onward:
  - All new changes to the guide must follow the **x.x.x regime** described in Chapter 5.
  - That is, any new version takes the form `1.MINOR.PATCH`, then `2.MINOR.PATCH`, and so on.

### 4.4 Checklist before Promoting to 1.0.0

Before performing the transition, validate:

- `\chapterscompletedof` and the chapter index correctly reflect the 1st edition's state (for example, they do not advertise chapters that do not yet exist).
- There are no obvious internal markers (like "TODO", "FIXME", temporary comments) in the main sections.
- Partial tables are clearly identified as such and do not look like errors.
- PROJECT-TRACKING is consistent with the state to be frozen as 1.0.0 (dates, versions, change descriptions).

---

## 5. Post-Publication Regime (≥ 1.0, x.x.x Scheme)

> From `1.0.0` onwards, the focus moves from internal development to edition and revision management for readers.

### 5.1 Semantics of Digits in x.x.x

After the first published edition, the guide uses:

```text
MAJOR.MINOR.PATCH
```

- **MAJOR (1st digit) — Guide edition.**  
  - Represents main editions (1st, 2nd, 3rd, …).
  - Should only change when there are broad enough changes to justify calling it a new edition.
  - Typical examples:
    - Large chapter reorganisation (merges, splits, strong order changes).
    - Addition/removal of large content blocks that alter global scope.
    - Adaptation to a new major BMS version requiring substantial rewrite of several chapters.

- **MINOR (2nd digit) — Compatible but substantial changes.**  
  - Marks important revisions, but still within the same edition.
  - A reader of the current edition does not get lost when moving to a new MINOR:
    - Index and overall structure remain recognisable.
  - Examples:
    - Addition of a new relevant chapter.
    - Large expansion of existing chapters (new sections and key tables).
    - Relevant internal reorganisation of a subset of chapters while keeping global architecture.

- **PATCH (3rd digit) — Smaller corrections and adjustments.**  
  - Logs fine-tuning within the same MINOR:
    - Spelling, grammar, formatting fixes.
    - Clarity improvements in paragraphs, captions, notes.
    - Small table, note, reference adjustments.
    - Local error corrections without large restructuring.

### 5.2 General Increment Rules in x.x.x

#### 5.2.1 General Principles

1. **Editorial compatibility.**  
   - If the reader can use the new version as a drop-in replacement for the previous one, without relearning global structure → generally not MAJOR.
   - If the new version requires rethinking stable references (chapter number, global order) → candidate for MAJOR.

2. **Frequency.**  
   - MAJOR is rare (editions).
   - MINOR is less rare, but still signals important revisions.
   - PATCH can happen more frequently (errata, polish).

3. **Continuity with 0.x.x.x.**  
   - 0.x.x.x becomes pre-publication history; in ≥ 1.0, avoid unnecessary architecture resets.

#### 5.2.2 "When to Increment (Post-Publication)" Table

| Situation | Inc. | Comment |
|----------|------|---------|
| Reorganise chapter structure (merges, splits, large order changes) | **MAJOR** | Reader sees it as a new edition of the guide. |
| Add/remove large content blocks that change global scope | **MAJOR** | For example, whole new part, or removal of a dominant part. |
| Adapt guide to a new major BMS version with substantial rewrite of several chapters | **MAJOR** | Old content is no longer fully current. |
| Add a new important chapter within the same edition | **MINOR** | Scope expands, edition remains the same. |
| Substantially expand one or more chapters (new sections, key tables) | **MINOR** | Significant improvement without breaking global organisation. |
| Reorganise internally a subset of chapters, keeping index recognisable | **MINOR** | Revised edition within same MAJOR. |
| Correct several localised content errors in text/tables | **PATCH** | Focus on fixing, not expanding scope. |
| Fix typos, grammar, improve clarity, update references | **PATCH** | Typical errata/polish versions. |
| Adjust few table cells, change labels without altering logic | **PATCH** | No chapter renumbering or flow changes. |

### 5.3 Role of Tables in ≥ 1.0

- Tables are part of chapters, not MAJOR artefacts:
  - A new large, central table in an important chapter:
    - May justify **MINOR**, if expansion is substantial.
    - Or **PATCH**, if it is just a refinement of already described content.

- Localised table corrections (cells, acronyms, notes):
  - Tend to be **PATCH**, unless the change is so broad that it modifies the logic of a key section (then evaluate MINOR).

### 5.4 Example Progression in x.x.x

#### 5.4.1 From the 1st Edition Onward

- `1.0.0` — 1st published edition.  
  - Stable chapter structure, usable narrative, tables present and clearly marked when partial.

- `1.0.1` — Initial errata.  
  - Typo fixes, small errors in TMS/DMS/CMS descriptions, localised formatting tweaks.

- `1.1.0` — Expanded revision within 1st edition.  
  - Addition of one new relevant chapter (for example, advanced training flows).
  - Some tables originally from 0.x.x.x have been completed.

- `1.1.3` — Third set of minor fixes on top of 1.1.0.  
  - `1.1.1`, `1.1.2`, `1.1.3` accumulate errata and clarifications.

- `2.0.0` — 2nd revised edition.  
  - Several chapters regrouped, order revised, broad updates to follow a new major BMS version.

#### 5.4.2 Decision Examples

- **Case 1 — New chapter "TMS/DMS/CMS in additional aircraft" in 1.x.**
  - Global structure stays recognisable → `1.0.2 → 1.1.0` (MINOR).  

- **Case 2 — Fixing incorrect commands in CMS tables.**
  - Cell-level fixes, no chapter restructuring → `1.1.0 → 1.1.1` (PATCH).  

- **Case 3 — Reorganising training part (Ch. 6) into two parts.**
  - If only part of structure changes, with recognisable index → MINOR.  
  - If it triggers wide architecture changes → evaluate MAJOR.  

### 5.5 Interaction with 0.x.x.x History

- 0.x.x.x versions:
  - Kept as pre-publication history, useful for understanding evolution and didactic decisions.  

- After `1.0.0`:
  - No new 0.* versions are created.
  - All future changes follow x.x.x regime.  

### 5.6 Quick Checklist for ≥ 1.0

1. Does your change alter the edition (reader should perceive it as a new edition)?
   - Yes → **MAJOR** (for example `1.3.2 → 2.0.0`).  
   - No → continue.

2. Does your change significantly expand scope or reorganise an important part, while staying in same edition?
   - Yes → **MINOR** (for example `1.0.0 → 1.1.0`).  
   - No → continue.

3. Is your change local (fixes, clarifications, small table/text adjustments)?
   - Yes → **PATCH** (for example `1.1.0 → 1.1.1`).  

---

## 6. Rules Common to Both Regimes

### 6.1 Build Date and Compilation

- Build date (`YYYYMMDD`) must be updated whenever:
  - A new version number (0.x.x.x or x.x.x) is established.  
  - A relevant snapshot is compiled and saved.  

- Difference between internal snapshot and official version:
  - Only versions whose number was updated in `\docversion` and in the snapshot file name enter PROJECT-TRACKING as milestones.  

### 6.2 File Naming and Snapshot Workflow

Single workflow for 0.x.x.x and x.x.x:

1. **Determine change type.**  
   - Use the appropriate "When to Increment" tables (pre- or post-publication).

2. **Update version/date macros in LaTeX.**  
   - Set `\docversion` to the new number.
   - Set `\docbuild` to the new `YYYYMMDD` date.
   - Ensure `\fulldocversion` reflects the correct combination.

3. **Compile and check for errors.**  
   - Generate the PDF and check LaTeX warnings/errors.

4. **Save the snapshot under `WIP/GUIDE/`.**  
   - Apply the pattern:

   ```text
   WIP/GUIDE/guide-vMAJOR.MINOR[.PATCH[.SUBPATCH]]-YYYYMMDD.tex
   ```

5. **Propagate to the canonical file.**  
   - Copy the new snapshot over `guide.tex` in the repository root so that Git/GitHub see the change as an update of the same file.

6. **Update PROJECT-TRACKING.**  
   - Add a line with version, date, affected chapter(s), and a concise description of the change.

7. **Archive previous snapshots.**  
   - Keep the earlier `guide-v*.tex` files in `WIP/GUIDE/` (optionally grouped under `/prepub/` or `/published/`), and keep or generate the matching PDFs.

### 6.3 Archival Strategy

- Organisation by regime (inside `WIP/GUIDE/` or subfolders):
  - `prepub/guide-v0.*.tex` — internal development history.  
  - `published/guide-v1.*.tex`, `published/guide-v2.*.tex`, etc. — published editions and revisions.  

- Git (optional but recommended):
  - Version `guide.tex` and other text files.
  - Exclude heavy artefacts via `.gitignore`, for example:

  ```text
  *.pdf
  *.docx
  *.aux
  *.log
  *.synctex.gz
  ```

### 6.4 Relationship with WIP File Naming

- This document (Version System v4.2) governs the versioning and naming of the **guide snapshots** (`WIP/GUIDE/guide-v*.tex`) and their relationship with the canonical `guide.tex` in the repository root.  
- Individual preparation files (`section-`, `table-`, `visual-`, `notes-`) follow their own rules defined in the separate `WIP-FILE-NAMING v*` document.  
- These WIP files only impact the guide version when their content is integrated into the current snapshot and propagated to `guide.tex`.

---

## 7. Consolidated Quick Reference

### 7.1 Quick Reference (0.x.x.x — Pre-Publication)

- **MAJOR = 0** always.  
- **MINOR:** new chapter enters guide.  
- **PATCH:** structural change in chapter (sections/tables altering flow).  
- **SUBPATCH:** fine-tuning (typos, wording, small table tweaks).  

| Key Situation | Pre Version (ex.) | Post Version (ex.) |
|---------------|-------------------|--------------------|
| New chapter enters guide | `0.1.4.0 → 0.2.0.0` | — |
| Restructure chapter sections | `0.2.1.0 → 0.2.2.0` | — |
| Important table changes chapter usage | `0.2.2.0 → 0.2.3.0` | — |
| Typos and micro wording fixes | `0.2.3.0 → 0.2.3.1` | — |

### 7.2 Quick Reference (x.x.x — Post-Publication)

- **MAJOR:** new edition (broad changes, potential incompatibility).  
- **MINOR:** compatible but substantial expansion (new chapters, large blocks).  
- **PATCH:** minor corrections, clarifications, localised adjustments.  

| Key Situation | Pre Version (ex.) | Post Version (ex.) |
|---------------|-------------------|--------------------|
| Second revised edition (broad change) | — | `1.3.2 → 2.0.0` |
| Important new chapter within same edition | — | `1.0.0 → 1.1.0` |
| Minor fixes and clarifications on 1.1.0 | — | `1.1.0 → 1.1.1` |

### 7.3 Key Notes

- Tables are always part of chapters; they never define MAJOR alone.  
- 0.x.x.x is never a published edition; it is always an internal development regime.  
- `1.0` marks the first published edition; `2.0`, `3.0`, etc., are successive editions, consistent with good technical documentation practice.  

---

**End of document — Version System v4.2**
