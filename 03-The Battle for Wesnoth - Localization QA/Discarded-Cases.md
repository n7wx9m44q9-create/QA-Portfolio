# Discarded Cases

## Purpose

This document records cases that initially appeared suspicious during exploratory testing but were investigated and intentionally not reported as defects.

Each case was evaluated using:

**Observation → Investigation → Finding → Decision**

The purpose is to demonstrate that potentially unusual wording, terminology, or behavior was not automatically classified as a defect without sufficient evidence.

---

## L10N-DISC-001 — "Has de seleccionar un héroe"

### Observation

The Tutorial uses the expression:

> Has de seleccionar un héroe.

The wording initially appeared unusual compared with more common modern Spanish constructions.

### Investigation

The expression `has de + infinitive` was reviewed in context.

It is grammatically valid Spanish and can express obligation. Its slightly formal or archaic tone is also compatible with the fantasy setting.

### Decision

**Discarded — valid localization.**

No objective linguistic error was identified.

---

## L10N-DISC-002 — "Torreón" as translation of "keep"

### Observation

The term `torreón` was initially considered potentially inconsistent as a translation of the English term `keep`.

### Investigation

The term was evaluated within the medieval/fantasy context and surrounding terminology.

`Torreón` is a valid Spanish word associated with a fortified tower or strong defensive structure and can function appropriately in this context.

### Decision

**Discarded — contextually valid terminology.**

The difference from a possible literal translation does not constitute a localization defect.

---

## L10N-DISC-003 — Combat damage calculation

### Observation

A Tutorial dialogue contained values involving unit hit points and damage.

The sequence appeared potentially suspicious because the dialogue described a unit with 17 HP receiving 3 damage multiple times.

### Investigation

The calculation was checked:

- Initial HP: 17
- Damage per attack: 3
- Five attacks: 3 × 5 = 15
- Remaining HP: 2

The values were mathematically consistent.

### Decision

**Discarded — calculation is correct.**

No localization or gameplay inconsistency was found.

---

## L10N-DISC-004 — Lowercase terminology in Help

### Observation

Terms such as:

> espada  
> arco  
> cuerpo a cuerpo

appeared in lowercase.

### Investigation

The terms were reviewed as common nouns rather than proper names or official UI labels.

Spanish common nouns are normally written in lowercase unless another capitalization rule applies.

### Decision

**Discarded — correct capitalization.**

No localization defect was identified.

---

## L10N-DISC-005 — "¡este estafermo!" after an ellipsis

### Observation

A dialogue sequence appeared to contain:

> … ¡este estafermo!

The capitalization initially appeared inconsistent.

### Investigation

The dialogue was reviewed as a continuation across separated text segments.

The apparent capitalization difference could be explained by the way the dialogue was segmented and presented rather than by an incorrect translation.

### Decision

**Discarded — no confirmed capitalization defect.**

The available evidence was insufficient to classify the text as incorrect.

---

## L10N-DISC-006 — "Termina tu turno" vs. "Finalizar turno"

### Observation

Different Tutorial strings use:

> Termina tu turno

and:

> Finalizar turno

The difference initially appeared to indicate inconsistent terminology.

### Investigation

The English source distinguishes between an instructional sentence such as:

> End your turn

and the UI command:

> End Turn

The Spanish forms correspond to these different contexts.

### Decision

**Discarded — contextually consistent.**

The difference is caused by the grammatical function of the source strings and does not represent a terminology defect.

---

## L10N-DISC-007 — "Chamana elfa"

### Observation

The expression `Chamana elfa` was initially considered potentially unusual as the Spanish equivalent of `Elvish Shaman`.

### Investigation

The term was checked against the game's established Spanish terminology.

`Chamana elfa` is consistent with the terminology used for the unit and faction.

### Decision

**Discarded — established terminology.**

No correction was justified.

---

## L10N-DISC-008 — "sección Juego de la ayuda"

### Observation

The expression `sección Juego de la ayuda` initially appeared potentially incorrect or incomplete.

### Investigation

The Help interface was inspected directly.

The corresponding Help section is actually named:

> Juego

Therefore, the expression refers to the section named `Juego` within the Help system.

### Decision

**Discarded — interface structure explains the wording.**

No localization defect was confirmed.

---

## L10N-DISC-009 — "tú" in Tutorial vs. "usted" in Help

### Observation

The Tutorial primarily addresses the player using informal `tú`, while some Help content uses formal `usted`.

### Investigation

The two areas were evaluated as different content contexts.

The Tutorial uses direct instructional/player-facing language, while Help content may use a different editorial register.

No mixed register was identified within the same Tutorial text as a general pattern.

### Decision

**Discarded — contextual register difference.**

The difference between sections alone is not sufficient evidence of a localization defect.

---

## L10N-DISC-010 — "legal", "caótico" and "neutral"

### Observation

Terms such as:

> legal  
> caótico  
> neutral

were initially considered potentially questionable terminology.

### Investigation

The terms were compared with the game's established Spanish terminology and glossary usage.

They correspond to established alignment terminology in the game.

### Decision

**Discarded — established terminology.**

No correction was justified.

---

## L10N-DISC-011 — "dificultad fácil" vs. "nivel Principiante"

### Observation

The interface contains references such as:

> dificultad fácil

and:

> nivel Principiante

The difference initially appeared to indicate inconsistent difficulty terminology.

### Investigation

The surrounding interface and campaign information were reviewed.

The terms refer to different concepts. Difficulty and campaign/scenario level classification are not necessarily the same attribute.

### Decision

**Discarded — different concepts.**

The presence of different terms does not by itself represent an inconsistency.

---

## L10N-DISC-012 — Different register between Main Menu tips

### Observation

Different Main Menu tips use different forms of address.

This initially suggested inconsistent use of `tú` and `usted`.

### Investigation

The tips were navigated individually using the available Previous/Next controls.

The review showed that register can vary from one independent message to another, but the messages themselves were generally internally consistent.

One specific tip did contain a mixed-register defect and was reported separately as **L10N-003**.

### Decision

**Discarded as a general pattern — contextual variation.**

Variation between independent messages was not treated as a defect. Only the message containing a mixed register within the same message was elevated to a bug.

---

## L10N-DISC-013 — "Tienda de campamento (C..."

### Observation

The interface displayed a truncated label similar to:

> Tienda de campamento (C...

The text initially appeared to be incomplete.

### Investigation

The UI was checked for overlap, clipping, or loss of access to the complete information.

The truncation uses an ellipsis to indicate that the text continues and does not overlap other interface elements.

### Decision

**Discarded — controlled truncation.**

The behavior is a UI presentation decision rather than a confirmed localization defect.

---

## L10N-DISC-014 — Truncated terrain names in Help navigation

### Observation

Several terrain names in the Help navigation were displayed in shortened form.

### Investigation

The selected entries were opened individually and the complete names were displayed in the main content area.

The truncation therefore does not remove access to the complete terminology.

### Decision

**Discarded — controlled truncation.**

The navigation could potentially be improved for distinguishability, but the observed behavior does not constitute a confirmed localization defect.

---

## L10N-DISC-015 — Save, Load and Autosave functionality

### Observation

Save/load behavior and autosave were included in the exploratory review because they are important game-state functions.

### Investigation

Manual saving, loading saved games, and autosave entries were tested during the campaign.

Saved-game information such as campaign, scenario, turn, date/time, and game version was displayed correctly.

### Decision

**Discarded — no defect observed.**

The tested save-related functions worked as expected.

---

## L10N-DISC-016 — Character dialogue after reaching 0 HP

### Observation

After a character reached:

> PV 0/58

a dialogue line appeared from that character:

> Todo está perdido ahora que he muerto...

This initially appeared contradictory because the character had already reached 0 HP.

### Investigation

The event was considered in the context of campaign dialogue and scenario progression.

The available evidence did not establish that the dialogue was incorrectly triggered. It may represent a narrative event or dialogue sequence associated with the character's defeat.

### Decision

**Discarded as a confirmed defect — insufficient evidence.**

The behavior was not elevated to a bug because the available evidence did not demonstrate an incorrect game state or localization error.

---

## General Decision Criteria

A case was discarded when investigation showed one or more of the following:

- the wording was grammatically valid;
- the terminology was established by the game;
- the apparent inconsistency was caused by different contexts;
- the behavior was intentional or controlled;
- the information remained accessible;
- the source text did not support an objective correction;
- the issue was subjective or dependent on regional preference;
- or there was insufficient evidence to establish a reproducible defect.

Discarding a case does not mean that the wording or behavior could never be improved.

It means that the available evidence did not justify reporting it as a defect within the scope of this QA cycle.
