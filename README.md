# TMS/DMS/CMS Usage Guide focused on Falcon BMS F-16 Flight Simulator

A comprehensive **LaTeX-based technical guide** documenting F-16 HOTAS switch systems (Throttle Management Switch, Data Management Switch, and Countermeasures Management Switch) for Falcon BMS F-16 Fligth Simulator.

The author is by no means affiliated to or endorsed by Falcon BMS or its developers. This guide is not an official Falcon BMS guide or manual. It's intended to help Falcon BMS Community.

---

## 📖 About This Project

This project develops a structured guide explaining HOTAS functionality across multiple F-16 blocks and international variants. The guide serves both novice and experienced pilots, covering conceptual frameworks, switch actuation, system interactions, and operational nuances grounded in Falcon BMS manuals (Dash-34, Dash-1) and training materials.

**Current Status:** Pre-publication phase (v0.x.x.x) — Chapter scaffolding and narrative consolidation underway.

---

## 📁 Project Structure

```
falcon-bms-hotas-tms-dms-cms-guide/
│
├── guide/                          # Active guide files (.tex)
│   ├── guide-v0.2.2.0-*.tex       # Current production version│   
│
├── TEMPLATES/                      # Structural templates & blueprints
│   ├── template-wip-V*.tex         # Canonical WIP file template
│   └── guide-structure-only-v*.tex # Chapter outline baseline
│
├── docs/                           # Governance & tracking (Markdown)
│   ├── Briefing document           # Project scope, style, layout rules
│   ├── Naming conventions          # Rules for WIP file naming & status
│   ├── Versioning system           # Guide version numbering & phases
│   ├── Project tracking            # Session log, WIP status, milestones
│   └── Training Mission Abb. Table # Table listing Training Mission Abbreviation for use in WIP and guide files
│
├── WIP/                            # Active work-in-progress files
│   ├── section-*.tex               # Chapter sections under development
│   ├── table-*.tex                 # HOTAS table scaffolds & content
│   ├── notes-*.md                  # Research notes & reference material
│   ├── visual-*.*                  # Diagrams, schematics 
│   └── ...                         # Other types
│
├── ARCHIVE/                        # Historical & approved files
│   ├── [completed WIP files]       # Sections integrated into guide
│   ├── [deprecated content]        # Intentionally retired material
│   └── [guide snapshots]           # Older guide versions for rollback
│
├── MISC/                           # General-purpose materials
│   ├── Reference documents         # External sources, notes
│   ├── Research materials          # Background & supporting info
│   └── Utilities & notes           # Miscellaneous project aids
│
├── FIG/                            # Images used in the Guide
│
├── WIP-version-name-generator.html # Interactive tool for WIP naming
├── md-to-docx-v3-1-0.bat           # Batch converter (Markdown → DOCX)
│
├── README.md                       # This file
└── CONTRIBUTUING.md                # Contributions Guide

```

---

## 📋 Key Documentation

### Governance Layer

The project uses **three integrated governance documents** (in `/docs/`) that define rules, structure, and workflows:

1. **Briefing Document**
   - Project scope, content outline, and style guidelines
   - Layout standards and table formatting rules
   - Current status & roadmap

2. **WIP Naming Conventions Guide**
   - Rules for organizing WIP files (sections, tables, visuals, notes)
   - Status lifecycle: dev → review → final → approved → deprecated
   - How to create and track new WIP files

3. **Versioning System Guide**
   - Guide version numbering (0.x.x.x pre-publication, x.y.z post-publication)
   - MAJOR/MINOR/PATCH/SUBPATCH semantics
   - Integration workflow from WIP to guide snapshots

4. **Project Tracking** (living document)
   - Session-by-session progress log
   - WIP status snapshot
   - Integration timeline & milestones
   - Current priorities & phases

All governance documents are available in **Markdown** (for editing) and **DOCX** (for sharing).

---

## 🔄 Workflow (WIP Files)

### For Contributors & Developers:

1. **Create**: Copy template from `TEMPLATES/` to `WIP/` folder
2. **Name**: Follow naming conventions (use interactive HTML tool in root if needed, or guides in `DOCS/`)
3. **Develop**: Edit file with status (`dev` → `review` → `final` → `approved`)
4. **Review**: Human review of narrative, accuracy, and style alignment
5. **Archive**: Integrate approved files into guide, move to `ARCHIVE/`
6. **Track**: Update project tracking document with new version & session log

### File Status Codes:
- **dev** — Draft stage; not ready for review
- **review** — Under human review; open for feedback
- **final** — Approved and ready for integration
- **approved** — Integrated into guide and archived
- **deprecated** — Intentionally retired or superseded

---

## 📊 Current Project State

| Metric | Value |
|--------|-------|
| **Guide Version** | v0.2.2.0 (layout-optimized) |
| **Total Chapters Planned** | 7 |
| **Chapters with Narrative** | 2/7 |
| **Chapters Scaffolded** | 4/7 |
| **Tables Populated** | 0% |
| **Phase** | 0 (Chapter scaffolding) |

---

## 🛠️ Tools & Utilities

### WIP Naming Generator
Interactive HTML tool in project root for generating compliant WIP file names based on chapter, section, status, and date.

### Markdown-to-DOCX Converter
Batch script (using Pandoc) to export governance documents from Markdown to DOCX format for convenient sharing and reading - see CONVERTER-SETUP.docx in `MISC/` for further instructions about the md converter bat file.

---

## 📚 Sources & References

This guide is grounded in:

- **TO 1F-16CMAM-34-1-1** — Falcon BMS Simlator F-16 Avionics & Weapons Manual (Dash-34)
- **TO 1F-16CMAM-1** — Falcon BMS Simlator F-16C/D Flight Manual (Dash-1)
- **Falcon BMS 4.38.1 Training Manual** — Falcon BMS Simlator training missions guide
- **F-16 Combat Aircraft Fundamentals Handbook** — USAF Multi-Command guidelines
- **Various online sources**

All technical claims are cross-referenced to these sources.

---

## 📜 License

This project is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose

**Under the following terms:**
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made

For full license details, see: [Creative Commons BY 4.0](https://creativecommons.org/licenses/by/4.0/)

---

## 👥 Credits & Acknowledgments

**Project Development:**
- Carlos "Metal" Nader — Project lead, content author
- AI Assistant (Perplexity Pro) — Structural guidance, governance framework, documentation

**Technical References:**
- Falcon BMS (official manuals & training materials)
- F-16 community knowledge & subject-matter experts

**Tools & Utilities:**
- Pandoc (Markdown conversion)
- TexMaker (tex document editor and compiler)
- Visual Studios Code (md files editing)
- Git/GitHub (version control)

---

## 🤝 Contributing

Contributions are welcome! If you have:

- **Content corrections** — Inaccuracies or outdated information
- **Structural improvements** — Layout, organization, or clarity suggestions
- **New sections** — Expanded coverage of HOTAS systems or variants
- **Testing feedback** — LaTeX compilation or PDF rendering issues

Please read CONTRIBUTING.md.

---

## 📞 Contact & Feedback

For questions, suggestions, or feedback about this guide, please:

- Open an issue in the repository
- Review the **Project Tracking** document (in `/DOCS/`) for current status
- Check the other **Governance Documents** (in `/DOCS/`) for workflow details
- Send the author an e-mail: carlos.snm@gmail.com
- Falcon BMS forum post: https://forum.falcon-bms.com/topic/32541/in-development-tms-dms-cms-usage-guide-public-project?_=1768013631558
- Sorry....no social media

---

## 📅 Project Timeline & Phases

| Phase | Duration | Target | Milestone |
|:-----:|----------|--------|-----------|
| **0** | Current  | v0.1.0 → v0.7.0 | All chapters scaffolded; layout locked |
| **1** | TBD | v1.0.0 → v1.0.x | HOTAS tables populated & validated |
| **2** | TBD | v2.0.0-RC → Stable | Final review & public release |

---

## 🔍 Quick Links

- **Active Guide** — `/guide.tex in Root directory/` (current production version)
- **Work in Progress** — `/WIP/` (sections, tables, visuals under development)
- **Governance Docs** — `/docs/` (briefing, naming, versioning, tracking)
- **Templates** — `/TEMPLATES/` (WIP template, guide scaffold)
- **Archived Content** — `/ARCHIVE/` (completed & deprecated files)
- **Utilities** — Root directory (naming generator, format converter)

---

**Last Updated:** 2026-01-09  
**Status:** Pre-publication v0.2.2.0  
**License:** CC BY 4.0