# The Battle for Wesnoth — Game Localization QA

Independent QA project focused on evaluating the **English → Spanish localization** of *The Battle for Wesnoth*, an open-source turn-based tactical strategy game.

The project was conducted independently as a portfolio case study, with emphasis on **localization quality, linguistic accuracy, terminology, register consistency, contextual meaning, and UI text presentation**.

---

## Project Overview

**Game:** The Battle for Wesnoth  
**Version:** 1.18.8  
**Target language:** Spanish  
**Testing type:** Localization QA / Exploratory Testing  
**Project status:** Completed

### Coverage

Testing focused primarily on the **Tutorial Campaign**, with additional exploratory coverage of selected content from **A Tale of Two Brothers**.

The investigation included:

- Tutorial dialogue and instructions
- Scenario victory and defeat messages
- Main Menu gameplay tips
- Help documentation
- Unit, faction, terrain, and game terminology
- Player-address and register consistency
- Grammar and punctuation
- Translation accuracy and contextual meaning
- UI text, truncation, and readability
- Save, load, and autosave functionality

---

# Results

The investigation produced three types of findings:

| Result | Count |
|---|---:|
| Confirmed localization defects | **4** |
| Localization observations / improvement opportunities | **8** |
| Investigated and discarded candidates | **16** |

### Confirmed defects

All four confirmed defects were reproducible and supported by contextual or source-text evidence.

| ID | Area | Issue |
|---|---|---|
| **L10N-001** | Tutorial | Inconsistent and ambiguous player address in defeat message |
| **L10N-002** | Tutorial | Ambiguous and inconsistent player address in victory message |
| **L10N-003** | Main Menu Tips | Mixed informal and formal player address |
| **L10N-004** | Campaign Dialogue | Incorrect question punctuation and missing definite article |

→ **[View confirmed bugs](Bugs.md)**

---

## Localization Observations

Several findings represented possible improvements in wording, clarity, or UX but did not meet the evidence threshold required to classify them as defects.

These included:

- ambiguous UI wording;
- awkward sentence construction;
- literal-sounding dialogue;
- victory-summary wording;
- controlled text truncation;
- and regional language considerations.

→ **[View localization observations](Localization-Observations.md)**

---

## Discarded Cases

Potential issues were investigated before deciding whether to report them.

Cases were discarded when the wording was valid, terminology was established, behavior was contextually correct, or available evidence was insufficient to support a defect.

Examples included:

- fantasy terminology such as `torreón`;
- `Chamana elfa`;
- `has de seleccionar un héroe`;
- `Termina tu turno` vs. `Finalizar turno`;
- differences between `tú` and `usted` across separate content contexts;
- controlled UI truncation;
- and save/load/autosave behavior.

→ **[View investigated and discarded cases](Discarded-Cases.md)**

---

# QA Approach

The investigation followed an evidence-based exploratory approach rather than treating every unusual translation as a defect.

### 1. Explore

The game was explored in English and Spanish to understand the relevant game context, dialogue, UI, terminology, and player-facing content.

### 2. Compare

Spanish strings were compared with the English source where available, while also considering the surrounding game context.

### 3. Validate

Potential issues were checked for:

- grammatical correctness;
- semantic accuracy;
- terminology consistency;
- player-address consistency;
- UI behavior;
- reproducibility;
- and contextual appropriateness.

### 4. Classify

Each finding was classified as one of:

**Confirmed defect → Localization observation → Discarded case**

This prevented subjective wording preferences from being reported as bugs without sufficient evidence.

---

# Key QA Takeaways

This project demonstrates practical experience with:

- Exploratory testing
- Localization QA
- English → Spanish source comparison
- Linguistic and grammatical validation
- Terminology analysis
- Register and consistency testing
- UI localization review
- Defect reproduction and documentation
- Evidence-based defect classification
- Distinguishing defects from wording improvements and false positives

A key part of the investigation was **knowing when not to report an issue**. Potentially unusual wording was investigated in context before being classified, helping avoid false positives and unsupported defect reports.

---

## Evidence

Screenshots supporting the confirmed defects are available in the [`Evidence`](Evidence/) folder.

---

## Project Context

This was an **independent portfolio project**, not a production assignment or contribution to the game's development team.

The objective was to simulate a realistic localization QA investigation and document the reasoning, findings, and evidence in a format suitable for professional QA work.
