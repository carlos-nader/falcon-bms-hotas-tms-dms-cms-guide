# Falcon BMS TMS/DMS/CMS HOTAS Usage Guide

A structured LaTeX-based reference guide for mastering the Target Management Switch (TMS), Display Management Switch (DMS), and Countermeasures Management Switch (CMS) in Falcon BMS 4.38.1.

## Project Overview

This project creates a professional, context-driven usage guide for three critical HOTAS switches in the F-16C/D aircraft modelled in Falcon BMS 4.38.1. The guide bridges the gap between official technical documentation (Dash-1, Dash-34, Training Manual) and practical, day-to-day virtual flying operations.

### What It Is

- A comprehensive reference organized by **master mode** and **sensor context**
- A collection of **context-sensitive tables** documenting each switch's behavior
- **Cross-referenced** to official BMS documentation and training missions
- Built with professional governance: version control, file naming standards, and project tracking

### What It Is Not

- A full HOTAS manual (focuses exclusively on TMS, DMS, CMS)
- A tactics textbook (tactical notes are brief and contextual only)
- Official Falcon BMS documentation (community effort, non-affiliated)

## Current Status (v0.2.2.0 — January 8, 2026)

| Aspect | Details |
|--------|---------|
| **Latest Version** | `v0.2.2.0+20260108` |
| **Master Guide File** | `guide-v0.2.2.0-20260108.tex` |
| **Chapters Complete** | 2 / 7 (Introduction, CMS Concept intro) |
| **Tables Populated** | 0% (architecture reserved, content pending) |
| **Development Phase** | Pre-publication (v0.x.x.x) |
| **Layout Standard** | Geometry Option D: A4, 2.0 cm side margins, 17.0 cm text width |

### Latest Updates

**v0.2.2.0 — Layout Optimization**
- Standardized page geometry to 2.0 cm left/right margins (2.5 cm top/bottom)
- Applied `hotastable` row height standard (`\arraystretch = 1.25`)
- Confirmed layout parameters for all future WIP sections

**v0.2.1.0 — CMS Chapter Structure**
- Refined Section 5 (CMS) with subsection layout
- Prepared scaffolding for CMS Actuation tables (5.2.1–5.2.4)

**v0.2.0.0 — CMS Introduction**
- Integrated Section 5.1 (CMS Concept and CMDS/ECM interaction)

## Repository Structure

```
projet-bms/
├── docs/
│   ├── BRIEFING-v0-1-4-1.docx           # Project specification & style guide
│   ├── VERSION-SYSTEM-V4.1.docx          # Semantic versioning rules
│   ├── WIP-NAMING-CONVENTION-v1.3.docx   # File naming standards
│   ├── PROJECT-TRACKING-v4.1.1.docx      # Timeline & status tracking
│   └── [Markdown versions coming]
│
├── WIP/                                  # Work-in-progress sections & tables
│   ├── section-C*.tex                    # Chapter sections under development
│   ├── table-*.tex                       # Standalone table WIP files
│   ├── visual-*.tex                      # Diagram and illustration WIP files
│   └── notes-*.tex                       # Development notes & research
│
├── ARCHIVE/                              # Approved WIP & historical versions
│   ├── guide-v0.1.0+20260105.pdf
│   ├── guide-v0.1.1+20260105.pdf
│   └── [... archived versions]
│
├── guide-v0.2.2.0-20260108.tex           # Current master guide source
├── README.md                             # This file
└── [Build outputs & auxiliary files]
```

## Versioning Scheme

The project uses a **4-part semantic versioning system** with two distinct regimes:

### Pre-Publication (0.x.x.x)

Used during scaffolding and content development:

- **MAJOR** = 0 (always)
- **MINOR** = chapter integration order
- **PATCH** = structural changes within chapters
- **SUBPATCH** = typos, wording, minor table refinements

**Current track:** `0.2.x.x` — CMS chapter structure underway

### Post-Publication (x.y.z, ≥ 1.0)

Used after first public release (`1.0.0`):

- **MAJOR** = edition number (1st, 2nd, 3rd...)
- **MINOR** = significant compatible revisions
- **PATCH** = corrections and polish

**Detailed rules:** See `VERSION-SYSTEM-V4.1.docx` in `docs/`

## Governance Documents

The project is governed by four key documents housed in `docs/`:

### 1. **BRIEFING** (v0.1.4.1)
Project specification: scope, style rules, layout parameters, content guidelines, and AI collaboration standards. Required reading for understanding what goes into the guide.

### 2. **VERSION-SYSTEM** (v4.1)
Authoritative rules for semantic versioning, file naming patterns, version increment triggers, and synchronization protocols across LaTeX macros, file names, and tracking documents.

### 3. **WIP NAMING CONVENTION** (v1.3)
Standardized naming for all work-in-progress files (chapters, sections, tables, notes, visuals) with status codes, organization rules, and automation hints.

### 4. **PROJECT TRACKING** (v4.1.1)
Session-by-session timeline, milestones, WIP file status, integration priority, and completion history. Updated at the end of each development session.

**Status:** Currently in `.docx` format. Markdown equivalents are planned to be published to `docs/` as the project progresses.

## File Naming Standards

The project enforces strict file naming conventions:

### Master Guide File
```
guide-vMAJOR.MINOR[.PATCH[.SUBPATCH]]-YYYYMMDD.tex
Example: guide-v0.2.2.0-20260108.tex
```

### Work-in-Progress (WIP) Files
```
[TYPE]-[CHAPTER]-[SECTION]-[COMPONENT]-[STATUS]-[DATE].tex
Example: section-C5-S2-cms-actuation-hotas-tables-review-2026-01-08.tex
```

**Types:** `section`, `table`, `visual`, `notes`  
**Status codes:** `wip` (active), `review` (under review), `approved` (ready for integration), `archive` (historical)

## Key Documents in the Guide

### Chapters (Planned Structure)

1. **Introduction** — Scope, authorship, sources, how to read
2. **HOTAS Fundamentals** — SOI, timing, master modes, overview table
3. **TMS — Target Management Switch** — Concept + all master modes and sensors
4. **DMS — Display Management Switch** — SOI architecture and MFDS format control
5. **CMS — Countermeasures Management Switch** — CMDS/ECM interaction and tables
6. **Training References and Practical Flows** — Mission progression, checklists
7. **HOTAS Visual Reference** — Stick/throttle diagrams with quick-reference labels

### Appendices

- Block / variant notes (differences across F-16CM variants)
- Tables index (cross-reference of all TMS/DMS/CMS tables)

## Content Structure: hotastable Format

All TMS/DMS/CMS behavior tables follow a standardized 7-column format:

| Column | Width | Purpose |
|--------|-------|---------|
| **State** | 1.6 cm | Master mode + sensor/weapon context |
| **Direction** | 1.0 cm | Hat direction: Up, Down, Left, Right |
| **Action** | 1.0 cm | Press type: Short, Long, Short repeated, Long hold |
| **Function** | 3.4 cm | What the switch does (informal title) |
| **Effect / Nuance** | 5.8 cm | Technical explanation + interactions |
| **Dash34** | 1.4 cm | Reference to BMS Dash-34 sections |
| **Train** | 1.4 cm | Recommended BMS training missions |

This format ensures consistent, dense, professional documentation while maintaining easy navigation.

## Technical Specifications

### LaTeX Configuration

- **Engine:** pdfTeX / XeLaTeX
- **Page Size:** A4 (210 × 297 mm)
- **Margins:** 2.0 cm (left/right), 2.5 cm (top/bottom)
- **Text Width:** 17.0 cm
- **HOTAS Table Width:** 15.6 cm (locked architecture)
- **Font:** Standard pdfTeX fonts + custom styling via `fancyhdr`, `longtable`, `array`

### Table Formatting (hotastable)

- **Font Size:** `\small` (10 pt)
- **Row Height:** `\arraystretch = 1.25`
- **Table Type:** `longtable` (allows multi-page tables with automatic breaks)

### Helper Macros

```latex
\dashref{section}      % Reference Dash-34 section, e.g., \dashref{2.1.5}
\dashone{section}      % Reference Dash-1 section
\trnref{mission}       % Reference training mission, e.g., \trnref{18 (BARCAP)}
\trnman                % Label for Falcon BMS Training Manual
\bmsver                % Current BMS version (4.38.1)
\dashrefs{s1, s2, ...} % Multiple Dash-34 references
```

## Sources and References

The guide is conceptually aligned with (but never reproduces) official Falcon BMS documentation:

- **TO BMS 1F-16CMAM-34-1-1** (Dash-34) — Avionics & Weapons Manual
- **TO BMS 1F-16CMAM-1** (Dash-1) — Flight Manual / Systems
- **Falcon BMS Training Manual 4.38.1** — 33 missions with learning objectives
- **Falcon BMS User Manual 4.38** — General systems reference

All content is paraphrased in original words. No copyrighted text is reproduced.

## Collaboration Model

**This is a personal documentation effort**, maintained transparently for the benefit of the Falcon BMS flight simulation community.

### Current Stage

- **Open for:** Review, structural feedback, and source validation
- **Not open for:** External contributions (until v1.0.0 public release)

After the first public release (`1.0.0`), external contributions will be considered under a to-be-determined contribution policy.

## How to Use This Repository

### For Developers / Contributors

1. Review the **BRIEFING** (`docs/BRIEFING-v0-1-4-1.docx`) for scope and style rules
2. Check the **VERSION-SYSTEM** for versioning decisions
3. Follow the **WIP NAMING CONVENTION** when creating new files
4. Update **PROJECT TRACKING** at the end of each session
5. Commit changes with clear messages referencing version and component

### For Readers

The final compiled guide (PDF) will be released with version `1.0.0`. Until then, the source `.tex` files and supporting documents in `docs/` provide insight into the project structure and technical approach.

## Build Instructions (Planned)

Build scripts and compilation instructions will be documented as the project stabilizes. For now, the project uses standard LaTeX tooling:

```bash
pdflatex guide-v0.2.2.0-20260108.tex
```

(Full build process with auxiliary files, index generation, and PDF optimization will be documented separately.)

## Timeline

| Version | Date | Milestone |
|---------|------|-----------|
| v0.1.0  | Jan 5, 2026 | Initial scaffolding |
| v0.1.4.0 | Jan 7, 2026 | Layout finalized |
| v0.2.2.0 | Jan 8, 2026 | CMS chapter structure, geometry standardized |
| v0.3.0.0 | *Planned* | Next chapter integration |
| **v1.0.0** | *TBD* | First public release |

## License & Disclaimer

This project is **non-affiliated with BMS Development Group** and is created for educational and reference purposes within the Falcon BMS community.

- The guide does not reproduce copyrighted Falcon BMS documentation
- All content is original and paraphrased
- Falcon BMS is © BMS Development Group; refer to official BMS documentation for authoritative information

## Contact & Feedback

This is a personal project. Feedback on structure, clarity, or technical accuracy is welcome through the repository's issue tracker (when available).

---

**Last Updated:** January 9, 2026 — README restructured with complete project overview, governance model, and technical specifications.

**Current Maintainer:** Project author (Brasília, Federal District, Brazil)  
**Project Status:** Pre-publication scaffolding (Phase 0) — v0.2.2.0