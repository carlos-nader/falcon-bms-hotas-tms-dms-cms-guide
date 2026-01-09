# Falcon BMS 4.38.1 — TMS, DMS and CMS Usage Guide: Project Brief

**Brief Version:** v0.1.4.1 (Layout Parameters Update — 08 January 2026)

## Project Title

**Falcon BMS 4.38.1 — TMS, DMS and CMS Usage Guide**

## Project Brief (For the Assistant)

You are helping build a structured LaTeX document called **"TMS, DMS and CMS Usage Guide for Falcon BMS 4.38.1"**. The final result should be a community, non‑official reference for the practical use of the F‑16 TMS, DMS and CMS switches in Falcon BMS 4.38.1.

**Important:**

- The human author will give instructions in **Portuguese**.
- All content that goes into the **document** (LaTeX text, tables, captions, etc.) must be in **English**.

---

## 1. Scope and Goals

- The guide focuses **only** on three HOTAS switches: **TMS, DMS and CMS**.
- Other HOTAS controls (for example NWS/MSL STEP, MAN RNG/UNCAGE, etc.) may be mentioned **only when strictly necessary** to understand TMS/DMS/CMS behaviour.
- The document is **not** a full HOTAS or full avionics manual; it is a *usage guide* for these three switches, organized by context and supported by tables.
- The language of the document is English; style is clear, concise and *manual‑like*, not chatty.

### Main Goals

- Reorganize information that is spread across the BMS Dash‑1, Dash‑34 and the BMS Training Manual into **context‑based tables** and short explanations.
- Make it easy for a virtual pilot to answer: *"In this mode/sensor/weapon, what does each direction of TMS/DMS/CMS do?"*
- Cross‑reference each table line to:
  - The relevant Dash‑34 (and sometimes Dash‑1) section.
  - One or more BMS training missions where the behaviour can be practised.

---

## 2. Sources to Align With (But Never Limited To)

When generating or refining content, conceptually align with (but do not copy):

### Falcon BMS Dash‑34 (TO BMS 1F‑16CMAM‑34‑1‑1)

Especially, but never limited to:

- Hands‑On Controls (HOTAS) section.
- SOI behaviour.
- Defensive avionics (ALE‑47, ECM, CMS).
- Weapon‑specific chapters (HARM, Maverick, IAMs, SPICE, Harpoon, etc.).

### Falcon BMS Dash‑1 (TO BMS 1F‑16CMAM‑1)

Where relevant (overall aircraft systems, master modes, etc.).

### Falcon BMS Training Manual 4.38.1

Especially, but never limited to:

- Mission descriptions and "learning objectives".
- Missions involving SEAD/EW, HARM, IAMs, LGBs, BARCAP, IFF, etc.

**Critical rule:** Never reproduce copyrighted text; always paraphrase in original words.

---

## 3. Document Structure (LaTeX Already Prepared)

Assume there is already a LaTeX template with this structure. Do **not** change the overall structure or helper macros unless explicitly requested, but suggestions may be made when technically justified. Always generate complete LaTeX files when ordered to generate one.

### Chapter Breakdown

**1. Introduction**

- 1.1 Scope and purpose.
- 1.2 Version, authorship and AI assistance.
- 1.3 Sources and references.
- 1.4 Document structure and how to read it.

**2. HOTAS Fundamentals**

- 2.1 Sensor of Interest (SOI) and display logic.
- 2.2 Short vs long presses and timing.
- 2.3 Master modes and context‑sensitive behaviour.
- 2.4 Overview of TMS, DMS and CMS.
- Table with: switch, location (stick/throttle), general role, detailed chapter.

**3. TMS — Target Management Switch**

- 3.1 Concept and general behaviour.
- 3.2 TMS and Situational Awareness displays (HSD, HSI, DED) — **NEW SECTION**.
  - 3.2.1 HSD cursor control and waypoint management.
  - 3.2.2 Integration with NAV master mode.
  - 3.2.3 Cross‑mode SA display interaction (A‑A, A‑G context).
- 3.3 TMS in Air‑to‑Air.
  - FCR CRM (RWS / ULS / VSR).
  - SAM / DT‑SAM.
  - TWS.
  - STT.
  - ACM (30×20, 10×60, BORE, SLEW).
  - IFF interrogations (SCAN / LOS).
- 3.4 TMS in Air‑to‑Ground — sensors and SPI.
  - FCR A‑G (GM / GMT / SEA / AGR).
  - TGP A‑G.
  - HUD / HMCS (SPI, Snowplow, CZ, VIP/VRP cues).
  - Markpoints and steerpoint management.
- 3.5 TMS in A‑G weapon employment.
  - Unguided bombs and rockets (CCIP / CCRP / DTOS).
  - EO weapons — Maverick (VIS / PRE / BORE).
  - IAMs (JDAM / JSOW / WCMD / SPICE / others).
  - LGBs and laser employment (single ship / buddy).
  - Anti‑radiation (HARM POS / HAS / HAD).
  - Naval weapons (Harpoon, others).
- 3.6 TMS — Block / variant notes.

**4. DMS — Display Management Switch**

- 4.1 Concept and Sensor of Interest (SOI).
  - 4.1.1 SOI definition and scope across displays.
  - 4.1.2 Role of the DMS in SOI selection.
  - 4.1.3 Example SOI flow (overview).
- 4.2 DMS in MFDS format selection and SWAP.
  - 4.2.1 MFDS format selection and cycling.
  - 4.2.2 SWAP and display management.
  - 4.2.3 HSD control via SOI and MFDS functions.
- 4.3 DMS in sensor and weapon context.
  - 4.3.1 SOI changes between FCR, TGP, HSD and HUD in Air‑to‑Air.
  - 4.3.2 SOI changes between FCR, TGP, HSD, HAD and WPN in Air‑to‑Ground.
  - 4.3.3 DMS with HARM — HAD page as SOI.
  - 4.3.4 DMS with IAMs and other weapon‑driven MFDS pages (SMS/WPN).
- 4.4 DMS — Block and variant notes.

**5. CMS — Countermeasures Management Switch**

- 5.1 Concept and interaction with CMDS / ECM.
  - 5.1.1 Concept.
  - 5.1.2 Interaction with CMDS / ECM.
- 5.2 CMS Switch Actuation — main table in subsections using `hotastable`.
  - 5.2.1 CMS Actuation with CMDS.
  - 5.2.2 CMS Actuation with ECM.
  - 5.2.3 CMS Consent & Constraints.
  - 5.2.4 Important Operational Notes.
- 5.3 CMS — Block and variant notes.

**6. Training References and Practical Flows**

- 6.1 How to use this guide with BMS training missions.
- 6.2 Recommended progression.
- 6.3 Example flows for typical missions.
- 6.4 Checklist: "what to practice next".
- Two‑column table: Topic × Recommended training missions.
  - Example: "TMS A‑A CRM" → TRN 18, TRN 17B.

**7. HOTAS Visual Reference**

- 7.1 F‑16 HOTAS overview.
  - Single illustrative figure of stick + throttle, **only** labelling TMS, DMS and CMS positions (no other buttons).
- 7.2 TMS diagrams.
  - Close‑ups of the TMS hat with arrows and short labels per direction, grouped by broad context (A‑A radar, A‑G sensors/SPI, SA displays).
- 7.3 DMS diagrams.
  - Close‑ups of the DMS hat showing SOI / format control directions.
- 7.4 CMS diagrams.
  - Close‑up of the CMS hat with arrows and short text per direction (up/left/right/aft) for CMDS/ECM interaction.

### Appendices

- Block / variant overview (how behaviour is the same or slightly different across main BMS F‑16 variants).
- Tables index (list of all major TMS/DMS/CMS tables and where to find them).

### LaTeX Preamble Already Includes

- Fonts, geometry, microtype.
- Clickable TOC and PDF bookmarks.
- Headers/footers via `fancyhdr`.
- Custom `hotastable` environment with columns (updated v0.1.3):
  - **State** (1.6 cm), **Direction** (1.0 cm), **Action** (1.0 cm), **Function** (3.4 cm), **Effect / Nuance** (5.8 cm), **Dash34** (1.4 cm), **Train** (1.4 cm).
- Helper macros: `\dashref{}`, `\dashone{}`, `\trnref{}`, `\trnman`, `\bmsver`, `\dashrefs{}`.
- `graphicx` with `fig/` as the figures folder.

---

## 4. Layout Parameters (Updated January 8, 2026)

### 4.1 Geometry Configuration (Guide Standard)

- Page: A4 paper.
- Left margin: **2.0 cm**.
- Right margin: **2.0 cm**.
- Top margin: **2.5 cm**.
- Bottom margin: **2.5 cm**.
- Available text width: **17.0 cm**.
- Standard HOTAS table width: **15.6 cm** (sum of column widths).
- Horizontal safety margin: **1.4 cm** between table and text width.

**Rationale:**

- 2.0 cm left/right margins are consistent with typical **technical manual** practice (including Falcon BMS Dash‑1 and Dash‑34 styling).
- Compared to the previous 2.5 cm margins, this layout:
  - Preserves a professional look while avoiding a cramped page.
  - Increases available width from 16.0 cm to 17.0 cm, providing more breathing room around the 15.6 cm‑wide HOTAS table.
  - Reduces the risk of overfull boxes and awkward `longtable` breaks.

### 4.2 Table Formatting Standard (hotastable)

- Font size: `\small` (10 pt).
- Row height multiplier: `\arraystretch = 1.25`.

**Rationale:**

- `\arraystretch = 1.25` slightly reduces vertical spacing relative to 1.3, improving page economy while preserving legibility.
- This value is within recommended ranges for dense technical tables using `longtable`.
- The combination of `\small` + `\arraystretch = 1.25` is the **project‑wide standard** for all TMS/DMS/CMS tables implemented via `hotastable`.

### 4.3 Scope of Application (Layout Standard)

- The geometry and `hotastable` parameters defined here apply to:
  - The **master guide file** (`guide-v*.tex`).
  - Any **standalone WIP section files** that define their own page geometry and HOTAS tables.
- Column widths for `hotastable` are considered **architecture‑locked** by this brief:
  - `L{1.6cm}`, `L{1.0cm}`, `L{1.0cm}`, `L{3.4cm}`, `L{5.8cm}`, `L{1.4cm}`, `L{1.4cm}`.
- Future layout tuning for HOTAS tables should be done **only** through:
  - Global page geometry (margins).
  - `\arraystretch` (row height), within a safe readability range.

**References:**

- Falcon BMS Dash‑1 (TO BMS 1F‑16CMAM‑1): margin and layout conventions for technical manuals.
- Falcon BMS Dash‑34 (TO BMS 1F‑16CMAM‑34‑1‑1): similar page geometry and table density.
- LaTeX `geometry` and `longtable` documentation: general recommendations for margin and row‑spacing settings in dense technical documents.

---

## 5. Style and Content Rules

### 5.1 General Style

- **Language:** English, neutral and technical, similar to a good community manual.
- **Length:**
  - Most sections: 2–4 short paragraphs.
  - Avoid long walls of text; use lists when they improve clarity.
- **Tone:**
  - Explanatory, not conversational; no "chatty" expressions.
- **Terminology:**
  - Always define an acronym on first use in the document (for example "Sensor of Interest (SOI)").
  - Use consistent naming: TMS, DMS, CMS, CMDS, ECM, IAM, TGP, FCR, etc.

### 5.2 Focus

**Focus:** Always keep **TMS, DMS and CMS** at the centre.

- Mention other controls or panels **only when strictly needed** to understand what these three switches are doing (for example, CMDS panel mode, RF switch position, etc.).
- Do not drift into full tactics textbooks. A short tactical note is allowed in the "Effect / Nuance" column or in a brief sentence, but the primary purpose is to document **what the hat does** in each context.

### 5.3 Intro and "How to Read" Sections

**Introduction should clearly explain:**

- The unofficial and community‑made nature.
- Scope (TMS/DMS/CMS only).
- The role of tables and training‑mission references.
- That the visual chapter is a quick reference, not the primary source of truth.

**"Document structure and how to read it" should:**

- Explain where the big tables are.
- Explain how to interpret the columns.
- Indicate where to look for training missions.
- Explain how to use the visual reference chapter together with the tables.

---

## 6. Column Filling Guidelines for hotastable (v0.1.3)

For every TMS/DMS/CMS table, use the following conventions.

### Column 1: State (1.6 cm)

- Describe the **condition or context** where this action applies, combining master mode and the relevant sensor/weapon.
- Use a short, structured format, for example:
  - A‑A CRM — FCR RWS.
  - A‑A ACM — BORE.
  - A‑G — FCR GM.
  - A‑G — TGP.
  - A‑G — HUD/HMCS SPI.
  - NAV — HSD.
  - IAM — PRE.
  - HARM — POS.
  - LGB — TGP.
- This column is the "address" of the behaviour; keep it concise.
- If the behaviour is the same in all submodes of a given master mode, it is acceptable to write, for example:
  - A‑A CRM — any.
  - A‑G — any FCR mode.

### Column 2: Direction (1.0 cm)

- Use physical directions of the hat: **Up**, **Down**, **Left**, **Right**.
- If a behaviour is truly independent of direction (rare), write **Any** and explain in *Effect / Nuance*.
- Do **not** include timing here.

### Column 3: Action (1.0 cm)

- Describe the **type of press**, usually:
  - **Short** — quick tap, up to about 0.5–0.6 s.
  - **Long** — press longer than about 0.5–0.6 s, when the simulator distinguishes short vs long.
- Variants:
  - **Short, repeated** — for cycling actions.
  - **Long (hold)** — for actions that only stay active while held.
- Timing hints may be added if important, for example: `Long (>0.5 s)`.
- Do not describe system behaviour here, only the nature of the press.

### Column 4: Function (3.4 cm)

- Provide a **short name** for what the switch does in that context, for example:
  - Bug / designate target.
  - Drop track / RTS.
  - Set / update SPI.
  - Break track / CZ.
  - Cycle SOI between MFDs.
  - Give ECM consent.
  - Update waypoint.
- Think of this as the row's "title" — what a pilot might say informally.

### Column 5: Effect / Nuance (5.8 cm)

- Brief explanation (1–3 short sentences) of what actually happens:
  - How radar/TGP/HUD state changes (lock type, SPI, SOI, etc.).
  - Interactions with other systems (CMDS AUTO/SEMI, ECM pod, IAM state, etc.).
  - Conditions or exceptions (for example "only with an existing track", "no effect if no target").
- Include nuances:
  - First press vs subsequent presses.
  - What happens when there is no valid target.
  - Very short tactical remarks if they help understanding the use.

### Column 6: Dash34 (1.4 cm)

- Reference the **most relevant sections** in Dash‑34 (or Dash‑1 when needed).
- Use macros instead of prose, for example:
  - `\dashref{2.1.5}` for HOTAS hands‑on controls.
  - `\dashref{2.7.1}` for CMS/ECM operation.
- Multiple sections can be comma‑separated: `\dashref{2.1.5}, \dashref{2.7.1}`.
- Keep it short and purely referential.

### Column 7: Train (1.4 cm)

- Link behaviour to one or more **BMS training missions**:
  - `\trnref{28 (SEAD-EW)}`.
  - `\trnref{12 (HARM)}`.
  - `\trnref{18 (BARCAP)}`.
  - `\trnref{11 (LGB)}`.
- If several missions cover the behaviour, list 2–3:
  - `\trnref{18 (BARCAP)}, \trnref{17B (IFF Intercept)}`.
- If there is no direct mission, either:
  - leave the column blank, or
  - reference the closest one and mention that in *Effect / Nuance*.

---

## 7. Rules for the HOTAS Visual Reference Chapter

- All figures are **illustrative**, not official; style should be schematic, similar to technical drawings.

### 7.1 F‑16 HOTAS Overview

- Show a generic stick + throttle layout.
- **Only label TMS, DMS and CMS** positions; do not label other buttons.
- Example caption: *"F‑16 HOTAS overview — TMS, DMS and CMS positions (illustrative, generic F‑16CM Block 50/52 layout)."*

### 7.2 TMS Diagrams

- Each diagram shows only the TMS hat, with arrows and very short labels per direction.
- Group diagrams by broad context, for example:
  - "TMS — Air‑to‑Air radar contexts".
  - "TMS — Air‑to‑Ground sensor/SPI contexts".
  - "TMS — Situational Awareness displays".
- The label for each direction must be consistent with the **Function** column in the corresponding tables.

### 7.3 DMS Diagrams

- Show the DMS hat with arrows and short labels, for example:
  - HUD/HMCS SOI.
  - Left/right MFD SOI/format cycling.
- Again, text must match the Function column in DMS tables.

### 7.4 CMS Diagrams

- Show the CMS hat with arrows and short labels, for example:
  - Up (manual programs).
  - Left (program 6).
  - Aft (ECM/CMDS consent).
  - Right (cancel AUTO, inhibit).
- Match labels with the CMS tables.

In all diagrams, keep text extremely short (a few words per arrow) and rely on the tables for detailed explanations.

---

## 8. Professional Standards for AI‑Assisted Content Development

### 8.1 Communication Principles

When collaborating on this project, the following communication standards apply:

1. **Professional rigour**  
   All analysis, recommendations, and structural proposals must be grounded in primary sources and technical accuracy, not assumptions or simplifications.

2. **No condescension**  
   Treat the human author as the subject‑matter expert and decision‑maker. The AI's role is to provide deep analysis, identify sources of potential error (including its own), and present options with supporting evidence — not to guide or direct.

3. **Error identification**  
   When the human corrects an analysis, acknowledge the correction explicitly, explain the flawed reasoning, and reference which sources or logic should have been consulted. This documents learning and improves future responses.

4. **Primary source grounding**  
   All statements about TMS/DMS/CMS behaviour must be traceable to:
   - TO BMS 1F‑16CMAM‑34‑1‑1 (Dash‑34).
   - TO BMS 1F‑16CMAM‑1 (Dash‑1).
   - BMS Training Manual 4.38.1.
   - BMS User Manual 4.38.

   Avoid inference or generalisation from partial information.

5. **Structural integrity**  
   When proposing changes to chapter organisation or section placement, analyse against:
   - The actual use cases (NAV, A‑A, A‑G, DGFT).
   - Which master modes rely on which switches.
   - Where functionality overlaps vs where it is exclusive.
   - The learning progression for virtual pilots.
   - Whether a display/feature is *primary* to that context or *incidental*.

6. **Explicit scope boundaries**  
   Clearly distinguish between:
   - What applies to all blocks/variants vs specific ones.
   - What is primary TMS/DMS/CMS function vs incidental.
   - What is in scope (these three switches) vs out of scope (other HOTAS controls).

### 8.2 Application Examples

**Session 1 — HSD section placement**

- *Initial error*: Proposed HSD section placement as 4.4 (after A‑G SPI, before weapons), framing it as an A‑G planning tool.
- *Correction*: HSD is a transversal NAV/PLANNING tool used across **all master modes**, with primary relevance in NAV, not as an A‑G‑specific feature.
- *Flawed reasoning*: Confused "tool used during A‑G missions" with "A‑G‑specific tool"; failed to distinguish between primary context (NAV) and incidental context (A‑G backup/reference).
- *Implication*: Section should appear early in Chapter 3 (after "Concept"), positioned as a transversal display that spans master modes, not in the A‑G subsection.
- *Learning*: Context of display use (master mode → then sensor → then purpose) should be the primary organising principle, not mission phase or tactical application.

**Session 4 — DMS structure decision**

- *Problem identified*: DMS structure was ambiguous (three candidate organisations: A, B, C).
- *Resolution methodology*: Used Dash‑34 (sections 2.1.5, 2.1.6.2–2.1.6.3, 2.1.7.5.4) as the authoritative arbiter.
- *Technical validation*: Confirmed that DMS is a **transversal SOI/MFDS manager**, not a sensor‑specific or mode‑specific switch.
- *Decision*: Adopted **Option B** ("Transversal SOI architecture") with Dash‑34 terminology.
- *Result structure*:
  - 4.1 Concept and Sensor of Interest (SOI).
  - 4.2 DMS in MFDS format selection and SWAP.
  - 4.3 DMS in sensor and weapon context.
  - 4.4 DMS — Block and variant notes.
- *Enforcement*: Two critical focus points: DMS does **not** perform tactical functions; NAV/A‑A/A‑G are contexts, not three different DMS implementations.

---

## 9. How to Work With This Brief

- The human author will issue **instructions in Portuguese**, for example:
  - "Preencha a seção 'CMS — Concept and interaction with CMDS / ECM' no LaTeX."
  - "Crie a tabela de ações do CMS para os modos AUTO/SEMI/MAN dentro do hotastable."
- The assistant should:
  - Generate or modify LaTeX snippets that fit cleanly into the existing template.
  - Keep sections, labels and references consistent with this brief.
  - Use the helper macros and the `hotastable` environment as defined.
  - Provide rigorous analysis grounded in primary sources.
- The assistant may **suggest** structural improvements grounded in technical analysis and primary sources, but should not apply them unless explicitly approved.

**When in doubt, ask concise clarification and wait for the answer before making large refactors.**

---

## 10. Version Control System (VERSION_SYSTEM_v4.1 — Overview)

This section provides a **high‑level overview** of the versioning model used for the TMS/DMS/CMS guide. The **authoritative rules** are defined in the standalone document **"Falcon BMS TMS/DMS/CMS Guide Version System v4.1"**. In case of any discrepancy between this brief and that document, **Version System v4.1 is the single source of truth**.

### 10.1 Purpose and Scope

- Ensure that the guide, its LaTeX sources and tracking documents use a **consistent versioning scheme**.
- Provide a quick reference so that AI‑assisted and human edits **do not invent ad‑hoc version numbers**.
- Clarify how the version macros in the LaTeX preamble relate to file names and to the project tracking document.

### 10.2 Naming Convention (Guide Master File)

The main guide file always follows this pattern:

```text
guide-vMAJOR.MINOR[.PATCH[.SUBPATCH]]-YYYYMMDD.tex
```

- `MAJOR`, `MINOR`, `PATCH`, `SUBPATCH` are non‑negative integers.
- `YYYYMMDD` is the **build date** (year, month, day).
- The LaTeX preamble of the guide must contain, at minimum:
  - `\newcommand{\docversion}{...}`.
  - `\newcommand{\docbuild}{YYYYMMDD}`.
  - `\newcommand{\fulldocversion}{\docversion+\docbuild}`.
- These fields must always match:
  - The version encoded in the **file name**.
  - The entry for that version in the **PROJECT‑TRACKING** document.

### 10.3 Two Regimes: Pre‑Publication (0.x.x.x) and Post‑Publication (≥ 1.0)

Version System v4.1 defines two distinct regimes:

**Pre‑publication regime (0.x.x.x):**

- Used while the guide is still being built and no public edition has been declared.
- `MAJOR = 0` always.
- `MINOR` roughly tracks the order in which chapters are integrated into the main guide file.
- `PATCH` marks **structural changes** within those chapters (new sections, reorganisation, major table changes).
- `SUBPATCH` records **small refinements** (typos, wording, small table cell adjustments) that do not change the overall architecture.

**Post‑publication regime (≥ 1.0, x.y.z):**

- Used after the first public edition (`1.0.0`) of the guide is declared.
- `MAJOR` = **edition number** of the guide (1st, 2nd, 3rd...).
- `MINOR` = significant but compatible revisions within the same edition.
- `PATCH` = local corrections and polish (errata, clarity, minor table fixes).

The exact decision tables for when to increment each digit are defined in **Version System v4.1** and should not be reimplemented here.

### 10.4 Quick Operational Rules

The following rules are intended as a **working checklist**; always refer to Version System v4.1 for the full logic and examples.

- **Only content integrated into the main guide file (`guide-v*.tex`) can change its version.**
  - Work done in WIP files (`section-`, `table-`, `visual-`, `notes-`) does not affect the guide version until it is integrated.
- **Pre‑publication (0.x.x.x):**
  - New chapter structure integrated into the guide → typically a **MINOR** increment.
  - Structural changes inside existing chapters (new sections, major table reorganisation) → typically a **PATCH** increment.
  - Typos, wording and small formatting fixes → typically a **SUBPATCH** increment.
- **Post‑publication (≥ 1.0):**
  - Widening scope or large reorganisations that feel like a new edition → **MAJOR** increment.
  - Substantial expansions within the same edition (new chapter, large content additions) → **MINOR** increment.
  - Local corrections, improved clarity, small table fixes → **PATCH** increment.
- **Build date (`\docbuild` and `YYYYMMDD` in the file name) is updated every time a new version number is established.**

For precise thresholds and edge cases, consult **Version System v4.1**.

### 10.5 Single Source of Truth and Synchronisation

To avoid divergence between different artefacts, the following three elements must always be synchronised whenever a new guide version is created:

1. **LaTeX macros** in the guide preamble:
   - `\docversion` and `\docbuild` must reflect the new version and build date.
2. **File name** of the main guide source:
   - Must match the version and date, for example `guide-v0.2.2.0-20260108.tex`.
3. **PROJECT‑TRACKING entry**:
   - Must record the same version number, date, affected chapters/sections, and a concise description of the changes.

If there is ever a conflict between this brief and the detailed rules, **Version System v4.1** takes precedence and must be used as the deciding reference.

---

## 11. Current Project Status (v0.2.2.0)

### 11.1 Version Summary

| Component              | Status                          | Details |
|------------------------|---------------------------------|---------|
| **Active Version**     | `v0.2.2.0+20260108`             | Master guide updated to Geometry Option D (2.0 cm left/right margins) and `hotastable` row height `\arraystretch = 1.25`. |
| **Chapters Complete**  | `2 / 7`                         | Chapter 1 (Introduction) and Chapter 5.1 (CMS Concept and interaction with CMDS/ECM) have complete narrative scaffolding; remaining chapters are in skeleton form. |
| **Tables Filled**      | `0 %`                           | All TMS/DMS/CMS `hotastable` structures reserved but not yet populated with full behaviour data. |
| **Phase**              | `0 (Pre‑publication)`           | Guide remains in scaffolding regime `0.x.x.x` as defined by Version System v4.1 (no public edition ≥ 1.0 yet). |
| **Layout Standard**    | `Geometry Option D applied`     | Global layout aligned: A4, 2.0 cm side margins, 2.5 cm top/bottom, 17.0 cm text width, and HOTAS tables fixed at 15.6 cm width with `\small` and `\arraystretch = 1.25`. |
| **Next Milestone**     | `v0.3.0.0 (planned)`            | Integration of the next fully scaffolded chapter into the main guide (third chapter brought to narrative completion under the pre‑publication regime). |

### 11.2 Key Changes from v0.1.4.0 to v0.2.2.0

The path from `v0.1.4.0` to the current `v0.2.2.0` can be summarised in three main steps:

1. **v0.2.0.0 — CMS Chapter Integration (Section 5.1)**

- Introduced Section 5.1 (CMS Concept and interaction with CMDS / ECM) into the main guide file.
- Established the conceptual and architectural foundation for the CMS chapter.

2. **v0.2.1.0 — CMS Chapter Structure Update**

- Refined the internal structure of Chapter 5 (CMS), including subsection layout around CMS Actuation, Consent & Constraints and Operational Notes.
- Prepared the chapter for detailed `hotastable` tables in Section 5.2.

3. **v0.2.2.0 — Layout Optimisation (Geometry Option D)**

- Updated the guide's page geometry to A4 with 2.0 cm left/right margins (2.5 cm top/bottom) and 17.0 cm usable text width.
- Standardised `hotastable` row height to `\arraystretch = 1.25` across the guide.
- Confirmed that all future WIP sections for TMS/DMS/CMS tables must inherit these layout parameters.

### 11.3 Archival & Traceability (Guide Versions)

The following guide versions have been archived to preserve the evolution of the document. Each entry corresponds to a LaTeX source file and, where applicable, a matching PDF snapshot stored in the archive structure.

- `guide-v0.1.0+20260105`.
- `guide-v0.1.1+20260105`.
- `guide-v0.1.2+20260105`.
- `guide-v0.1.3+20260105`.
- `guide-v0.1.4.0+20260107`.
- `guide-v0.2.1.0-20260108`.

These historical versions provide traceability for structural decisions, early chapter scaffolding and geometry fixes made before the current 0.2.x.x series.

---

**Last Updated (Brief):** 08 January 2026 — Layout parameters section added, Version System v4.1 overview integrated, and project status updated to `v0.2.2.0`.