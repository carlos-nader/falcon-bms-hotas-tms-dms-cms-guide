# Contributing to TMS/DMS/CMS Usage Guide focused on Falcon BMS F-16 Flight Simulator

Thank you for your interest in contributing to this project! This document provides guidelines and instructions for making meaningful contributions.

---

## 🎯 Ways to Contribute

### Content & Technical Accuracy
- Report inaccuracies in HOTAS procedures or descriptions
- Suggest clarifications or rewording for better understanding
- Propose new sections or expanded coverage of HOTAS systems
- Provide corrections based on hands-on experience or official documentation

### Structural & Layout Improvements
- Suggest improvements to document organization or readability
- Report formatting issues, typos, or visual inconsistencies
- Propose better table layouts or visual presentations
- Identify missing cross-references or broken links

### Testing & Validation
- Test LaTeX compilation and PDF rendering
- Report rendering issues on different PDF readers
- Verify that procedures match current Falcon BMS F-16 Flight Simulator behavior
- Test links to external references and documentation

### Documentation & Governance
- Improve naming conventions or workflow documentation
- Suggest enhancements to governance rules
- Propose automation improvements or tooling suggestions
- Help organize or categorize research materials

---

## 📋 Before You Contribute

### Read These First:
1. **Naming and Versioning Guides** (in `/docs/`) — Understand how WIP files are organized and named
2. **Briefing Document** (in `/docs/`) — Review project scope, style rules, and content guidelines
3. **Project Tracking** (in `/docs/`) — Check current priorities, phase, and status
4. **This Guide** — You're reading it now!

### Get Familiar With:
- The **WIP/** folder structure (where active work lives)
- The **TEMPLATES/** folder (canonical template for new WIP files)
- Current guide version in **root directory**
- The **ARCHIVE/** folder (to see examples of completed work)

---

## 🔄 Contribution Workflow

### For Content & Technical Contributions:

#### **Option A: Report Issues & Suggestions** (Easiest)

1. **Email** a detailed description to: **carlos.snm@gmail.com**
   - Subject line: `[BMS Guide] [Type] Brief Description`
   - Example: `[BMS Guide] [Correction] CMS AUTO mode should persist after MAN override`
   
2. **Include:**
   - What needs to change (section/table/concept)
   - Why (inaccuracy, clarity, missing info)
   - Reference to official documentation if available (Dash-34 section, Training Manual, etc.)
   - Suggested wording or fix (if you have one)

3. **Wait for feedback** — Project maintainer will review and decide on integration

#### **Option B: Create WIP File** (For Substantial Contributions)

1. **Prepare your content:**
   - Copy template from `TEMPLATES/template-wip-V1.0.tex` to your local `/WIP/` folder
   - Rename following the naming convention (use the HTML naming generator in project root if needed)
   - Fill with your content following the **Briefing Document** style rules

2. **File naming example:**
   ```
   section-C5-S4-cms-training-procedures-dev-2026-01-15.tex
   ```
   (Chapter 5, Section 4, status "dev", date 2026-01-15)

3. **Set status appropriately:**
   - `dev` if the content is in its first and initial draft (inteded for when AI firt generates material for human review)
   - `review` when under human revision

4. **Email to: carlos.snm@gmail.com**
   - Subject: `[BMS Guide] [WIP Submission] Your File Name`
   - Attach your `.tex` file or provide a link to your fork/branch
   - Explain what the contribution covers and why it's needed
   - Highlight any dependencies or related WIP files

5. **Review & Integration:**
   - Maintainer will review for accuracy, style, and alignment with governance
   - Feedback will be provided via email
   - Once approved, your file moves to `final` status and integration into the guide

### For Governance & Infrastructure Contributions:

1. **Email your suggestion** to: **carlos.snm@gmail.com**
   - Subject: `[BMS Guide] [Governance/Infrastructure] Your Topic`
   - Describe the improvement and how it benefits the project

2. **Provide:**
   - Detailed explanation of the change
   - How it improves the workflow or documentation
   - Any examples or mockups if applicable

3. **Discussion & Decision:**
   - Maintainer will review and discuss via email
   - Changes to governance documents are carefully considered
   - Accepted changes will be integrated and tracked in **Project Tracking**

---

## ✅ Quality Standards

All contributions should meet these criteria:

### Content Quality:
- ✅ **Accurate** — Grounded in Dash-34, Dash-1, or Training Manual
- ✅ **Clear** — Written for both novice and experienced pilots
- ✅ **Complete** — Includes necessary context and cross-references
- ✅ **Consistent** — Follows style and terminology from existing sections
- ✅ **Formatted** — Uses standard `hotastable` environment for tables (see BRIEFING)

### Technical Quality:
- ✅ **Valid LaTeX** — Compiles without errors or warnings (where applicable)
- ✅ **Tested** — PDF renders correctly on standard PDF readers
- ✅ **Accessible** — Tables and content are readable and well-organized
- ✅ **Referenced** — All claims include Dash-34/Dash-1/Training Manual citations

### Governance Compliance:
- ✅ **Properly Named** — Follows WIP-FILE-NAMING conventions
- ✅ **Templated** — Uses canonical template from `/TEMPLATES/`
- ✅ **Documented** — Includes metadata block with author, date, status
- ✅ **Status Tracked** — File status is accurate (dev/review/final)

---

## 📧 Communication Guidelines

### Email Etiquette:
- **Subject line:** Always use format `[BMS Guide] [Type] Description`
- **Be specific:** Provide context, examples, references
- **Be concise:** Lead with the main point; details follow
- **Attach files:** Include `.tex`, `.md`, or `.docx` files (don't embed long content in email body)
- **Response time:** Allow 3–7 days for feedback (project is maintained by one person)

### Types to Use in Subject Line:
- `[Correction]` — Factual or technical inaccuracy
- `[Clarification]` — Request for clearer wording or explanation
- `[Suggestion]` — Idea for new content or improvement
- `[WIP Submission]` — Formal submission of a WIP file for review
- `[Governance]` — Changes to naming, versioning, or workflow rules
- `[Infrastructure]` — Tools, automation, or repo structure improvements
- `[Question]` — General question about the project or contribution process

---

## 🚫 What NOT to Contribute

Please **do not** submit:

- **Promotional content** — Links, ads, or self-promotion
- **Unverified claims** — Content not grounded in official documentation
- **Off-topic material** — Content unrelated to F-16 HOTAS in Falcon BMS
- **Large binary files** — Videos, images (unless essential and optimized)
- **Machine-generated text** — Without human review and editing
- **License conflicts** — Material incompatible with CC BY 4.0

---

## 📚 Project Resources

### Key Documents (in `/docs/`):
- **Briefing Document** — Project scope, style, layout rules
- **Naming Conventions** — WIP file naming & status lifecycle
- **Versioning System** — Guide version numbering & integration workflow
- **Project Tracking** — Current status, milestones, session log

### Templates & Examples (in `/TEMPLATES/`):
- **Canonical WIP Template** — Base structure for new WIP files
- **Guide Structure Scaffold** — Chapter outline example

### Source Materials:
- **TO 1F-16CMAM-34-1-1** (Dash-34) — Official avionics manual
- **TO 1F-16CMAM-1** (Dash-1) — Official flight manual
- **Falcon BMS 4.38.1 Training Manual** — Training missions & procedures
- **F-16 Combat Aircraft Fundamentals** — USAF operational handbook

All source materials should be cited in contributions.

---

## 🎓 Learning Path for New Contributors

**If you're new to the project:**

1. **Start here** — Read this CONTRIBUTING.md file completely
2. **Understand scope** — Review the Briefing Document (overview section)
3. **Learn structure** — Explore `/WIP/` and `/ARCHIVE/` to see examples
4. **Review template** — Copy and study `TEMPLATES/template-wip-V1.0.tex`
5. **Check status** — Read Project Tracking to understand current phase
6. **Submit suggestion** — Email a small suggestion or correction first (low barrier)
7. **Build confidence** — Once feedback loop is established, consider larger contributions

---

## ✨ Recognition

Contributors will be recognized in:
- **Project Tracking** — Session log noting contributor name/submission
- **Guide Credits** — Section 7 of main guide (contributors & acknowledments)
- **README.md** — Credits & acknowledgments section (for substantial contributions)

We value all contributions, from small corrections to major new sections!

---

## 📞 Contact

**Email:** carlos.snm@gmail.com
**Falcon BMS Forum Post:** https://forum.falcon-bms.com/topic/32541/in-development-tms-dms-cms-usage-guide-public-project?_=1768013631558

**How to reach out:**
- Report issues or suggest improvements
- Submit content for review
- Ask questions about the contribution process
- Propose governance or infrastructure changes

---

## 📄 License Reminder

All contributions are released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

By contributing, you agree that your work can be:
- Shared and redistributed in any medium
- Adapted and built upon by others
- Used for any purpose (commercial or non-commercial)

**As long as:** Original creator(s) are given credit.

For details, see: [CC BY 4.0 License](https://creativecommons.org/licenses/by/4.0/)

---

**Thank you for helping make this guide better!** 🙏✈️

**Last Updated:** 2026-01-09  
**Status:** Active (contributions welcome)  
**Maintainer:** Carlos Nader (carlos.snm@gmail.com)