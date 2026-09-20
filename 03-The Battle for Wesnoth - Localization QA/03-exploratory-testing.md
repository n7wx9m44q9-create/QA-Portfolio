# Exploratory Testing Notes

## Purpose

Document observations and findings from exploratory localization testing of **The Battle for Wesnoth**.

The exploratory approach was designed to:

1. Understand the game's flow and contextual meaning before evaluating the localization.
2. Explore the Tutorial Campaign in English and Spanish.
3. Compare English source content with the Spanish localization.
4. Identify localization issues involving meaning, grammar, terminology, consistency, player address, and UI presentation.
5. Investigate potentially suspicious translations before reporting them.
6. Reject candidates when available evidence does not demonstrate an objective localization defect.
7. Expand coverage when new, reproducible testing opportunities are discovered.

The objective is not to maximize the number of reported defects, but to identify reproducible localization issues while documenting the reasoning behind both confirmed and rejected findings.

---

# Environment

| Item | Value |
| --- | --- |
| Game | The Battle for Wesnoth |
| Version | 1.18.8 |
| OS | macOS |
| Platform | Desktop |
| Source language | English |
| Target language | Spanish |

---

# Phase 1 — English Exploration

## Tutorial Access

The Tutorial Campaign was used as the initial controlled area for exploratory testing.

The English version was explored first to establish contextual knowledge of:

- Scenario flow
- Objectives
- Character roles
- Unit types
- Gameplay instructions
- Dialogue context
- Victory and defeat conditions
- Relevant UI terminology

This contextual baseline was then used during the Spanish localization review.

---

## Tutorial Structure

The Tutorial consists of two scenarios designed to introduce the player to the game's basic mechanics.

| Scenario / Section | Objective | Main Mechanics | Relevant Characters / Units | Notes |
| --- | --- | --- | --- | --- |
| Tutorial Scenario 1 | Introduce the basic gameplay flow | Movement, attack, health, recruitment and basic interaction | Konrad / Lisar, Delfador and tutorial units | Used as the initial English and Spanish comparison area |
| Tutorial Scenario 2 | Continue the tutorial and introduce additional gameplay concepts | Recruitment, recalling experienced units, healing and additional unit types | Konrad / Lisar, Delfador, Elvish Archers and Elvish Shamans | Provided additional terminology and player-address coverage |

---

# Scenario Notes

## Scenario 1

### Context

The first Tutorial scenario introduces fundamental gameplay mechanics and provides instructions through tutorial messages and character dialogue.

### Areas observed

- Movement
- Attacking
- Health and damage
- Recruitment
- Character selection
- Tutorial instructions
- Dialogue
- Victory / defeat messaging
- Relevant UI terminology

### Localization observations

The Spanish localization generally preserved the meaning and context of the English content.

Particular attention was given to:

- Player address (`tú` / `usted`)
- Gender and number agreement
- Gameplay terminology
- Character and unit names
- Instructional wording
- Numeric values
- Victory and defeat messages

---

## Scenario 2

### Context

The second Tutorial scenario introduces additional mechanics and terminology.

### Areas observed

- Recalling experienced units
- Healing
- Additional recruitable unit types
- Scenario objectives
- Alignment terminology
- Help references
- Victory conditions
- Dialogue and instructional text

### Localization observations

The Spanish localization remained generally understandable and contextually appropriate.

Several potentially suspicious translations were investigated during this phase. Most were rejected after comparison with the English context, terminology references, or in-game behavior.

---

# Phase 2 — Spanish Exploration

The Tutorial flow was repeated and explored in Spanish after the English baseline had been established.

The Spanish exploration focused on:

- Translation accuracy
- Grammar and spelling
- Gender and number agreement
- Player-address consistency
- Terminology consistency
- Contextual meaning
- UI text
- Victory and defeat messages
- Help references
- Unit and character terminology
- Readability

---

## Language and Register

A recurring area of investigation was the form of address used for the player.

The Tutorial predominantly uses informal second-person forms (`tú`), including examples such as:

- `has`
- `puedes`
- `estás`
- `te`
- informal imperative forms such as `termina`

This register was used as a reference when evaluating other Tutorial messages.

Differences in register between separate product areas were not automatically treated as defects. The surrounding context was considered before reporting an issue.

---

# Language Switching

## English → Spanish

The game was tested using English as the source language and Spanish as the target language.

The English version was used to establish contextual meaning before evaluating potentially ambiguous Spanish translations.

## Spanish → English

The localization was also considered in reverse when validating whether observed Spanish wording corresponded to the intended English meaning.

## Persistence After Restart

Language persistence was considered as part of the localization smoke-testing process.

No confirmed localization defect related to language persistence was identified during the exploratory session.

---

# Main Menu Tips Exploration

During exploratory testing, the main menu tips were initially considered difficult to review systematically because they can appear as rotating/random content.

A reproducible review method was later identified: the `Anterior` and `Siguiente` buttons allow the available tips to be browsed manually.

This enabled a systematic review of the available Spanish tips.

The review identified one confirmed localization defect:

- **L10N-003** — One tip mixes informal and formal player address within the same message.

Other differences in register between separate tips were investigated but were not reported as defects because each individual message remained internally consistent.

---

# Confirmed Exploratory Findings

| ID | Finding | Language | Location | Reproducibility | Decision |
| --- | --- | --- | --- | --- | --- |
| L10N-001 | `¡Le han derrotado!` uses an ambiguous/inconsistent player address | Spanish | Tutorial → Defeat Message | Reproducible | **Confirmed defect** |
| L10N-002 | `¡Ha vencido!` uses an inconsistent player address and leaves the subject ambiguous | Spanish | Tutorial → Victory Message | Reproducible | **Confirmed defect** |
| L10N-003 | `tus unidades... agrúpelos... use...` mixes informal and formal player address within the same tip | Spanish | Main Menu → Tips | Reproducible | **Confirmed defect** |

---

# Investigated and Rejected Candidates

During exploratory testing, several potential localization issues were investigated but were not reported as defects because the available evidence did not demonstrate an objective, reproducible localization problem.

| Candidate | Observed text / behavior | Investigation | Decision |
| --- | --- | --- | --- |
| `… ¡este estafermo!` | Lowercase after an ellipsis | The dialogue was split across multiple text segments. The lowercase form was compatible with continuation of the previous sentence/dialogue. | **Rejected** |
| `Termina tu turno` / `Finalizar turno` | Different Spanish expressions for ending a turn | The English source distinguishes the instructional sentence `End your turn` from the UI command `End Turn`. The Spanish distinction therefore mirrors the source context. | **Rejected** |
| `cualquiera de los bandos` | `Es demasiado profunda para que cualquiera de los bandos pueda cruzarla...` | The wording may sound less natural than alternative formulations, but it remains grammatically valid and understandable. No objective translation error was established. | **Rejected** |
| `Chamana elfa` | `Elvish Shaman` → `Chamana elfa` | The original unit name and established Wesnoth terminology were considered. The term does not constitute a localization error in this context. | **Rejected** |
| `sección Juego de la ayuda` | Reference to the `Juego` section of Help | The Help section is actually named `Juego`, so the reference is functional despite sounding somewhat awkward. | **Rejected** |
| `tú` vs. `usted` between Tutorial and Help | Tutorial uses `tú`; Help uses `usted` | The areas have different contexts and the difference does not constitute an inconsistency within the same text. | **Rejected** |
| `dificultad fácil` / `nivel Principiante` | Different terminology for difficulty and campaign level | The two terms refer to different concepts in Wesnoth's campaign structure. | **Rejected** |
| `Legal` / `Caótico` / `Neutral` | Alignment terminology | The terminology was checked against the established Spanish localization terminology. | **Validated** |
| `echaremos en falta` | Regional variation in Spanish usage | The expression is grammatically valid. Regional preference alone does not establish a localization defect without a defined target locale requiring another form. | **Rejected / Regionalization observation** |
| `has de seleccionar` | `Has de seleccionar un héroe` | The construction may sound formal or archaic to some Spanish speakers, but it is grammatically valid and compatible with the game's fantasy/medieval tone. | **Rejected** |
| Numeric damage calculation | `17 → 2` after five attacks of 3 damage | The calculation was verified: `17 - (3 × 5) = 2`. | **Validated** |
| Register differences between individual main-menu tips | Some tips use `tú` while others use `usted` | All available tips were reviewed using `Anterior` and `Siguiente`. The mixed register was found only within L10N-003; the other messages were internally consistent. | **Rejected as individual defects** |

---

# QA Decision Principle

Potentially unusual wording was not automatically classified as a defect.

A candidate was reported only when the available evidence demonstrated a reproducible and objective localization problem involving one or more of the following:

- Translation accuracy
- Grammar
- Spelling
- Gender or number agreement
- Player-address consistency
- Terminology consistency
- Contextual correctness
- UI localization
- Ambiguity that affects clarity

Linguistic preference alone was not considered sufficient evidence for a defect.

When a suspicious translation could be explained by context, established terminology, source-language structure, or valid regional usage, it was documented and rejected rather than reported.

---

# Key Exploratory Observations

## Localization Quality

The Spanish localization was generally coherent and understandable throughout the Tutorial coverage.

Most potentially suspicious strings required contextual investigation before a decision could be made.

## Player Address

Player-address consistency was the most significant recurring localization issue identified during exploratory testing.

The confirmed defects were:

- L10N-001 — defeat message
- L10N-002 — victory message
- L10N-003 — main-menu tip

These defects occur in different UI/content contexts and were therefore reported separately.

## Terminology

Several terms that initially appeared questionable were validated against context or established terminology rather than being reported based solely on personal linguistic preference.

---

# Coverage Limitations

The exploratory session focused primarily on:

- Tutorial Campaign
- English → Spanish localization
- Main-menu tips
- Relevant Tutorial UI
- Tutorial dialogue and instructional content

The following areas were not covered in this exploratory pass:

- Other campaigns
- Multiplayer
- Map editor
- User-made content / add-ons
- Other languages
- Other platforms

---

# Next Exploration Phase

The next exploratory phase will extend localization testing beyond the Tutorial Campaign into the first non-Tutorial campaign.

The same methodology will be maintained:

1. Establish contextual understanding.
2. Explore the English content.
3. Explore the Spanish localization.
4. Compare source and target content.
5. Investigate suspicious translations.
6. Validate before reporting.
7. Document both confirmed defects and rejected candidates.

The objective remains evidence-driven defect discovery rather than maximizing the number of reported issues.

---

# Notes

This document records observations and decisions made during exploratory testing.

It should not be treated as official product documentation.

Its purpose is to establish practical contextual knowledge, document exploratory coverage, and provide traceability for the localization testing performed in this project.
