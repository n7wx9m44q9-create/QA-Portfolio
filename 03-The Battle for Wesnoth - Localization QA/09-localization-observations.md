# Localization Observations

## Purpose

This document records localization and linguistic observations identified during exploratory testing that were not elevated to confirmed defects.

These findings represent possible improvements in wording, clarity, readability, or localization quality. However, the available evidence was not sufficient to classify them as defects.

The investigation process followed:

**Observation → Investigation → Finding → Decision**

---

## L10N-OBS-001 — Ambiguous UI label: "Desplazamiento hacia..."

### Context

In the **Lista de unidades** interface, the following action was displayed:

> Desplazamiento hacia...

### Investigation

The action was tested to determine its actual behavior.

After selecting a unit and using the button, the window closes and the map centers on the selected unit.

### Finding

The functionality works correctly, but the label does not clearly communicate the resulting action.

Possible alternatives could include:

- `Centrar unidad`
- `Centrar en unidad`
- `Ir a la unidad`
- `Mostrar unidad en el mapa`

### Decision

**Localization / UX observation — not elevated to bug.**

The current wording is understandable and the functionality works correctly. The observation concerns clarity of the interface label rather than an incorrect localization.

---

## L10N-OBS-002 — Awkward construction in Help: "Además de en las eras principales..."

### Context

In the **Eras** section of Help, the following sentence was observed:

> Además de en las eras principales que vienen con el juego, hay disponibles muchas facciones creadas por los usuarios en los complementos.

### Investigation

The sentence was reviewed for grammatical structure, readability, and naturalness in Spanish.

The intended meaning remains understandable, but the construction `Además de en...` produces an awkward sentence structure.

### Finding

A more natural formulation could be:

> Además de las facciones incluidas en las eras principales que vienen con el juego, hay muchas facciones creadas por los usuarios disponibles en los complementos.

### Decision

**Localization observation — not elevated to bug.**

The original sentence is understandable and does not prevent the user from understanding the information. It was therefore classified as a wording improvement rather than a confirmed defect.

---

## L10N-OBS-003 — Literal-sounding dialogue construction

### Context

During the campaign **A Tale of Two Brothers**, the following dialogue was observed:

> ¡Señor, nuestros exploradores nos informan de que Baran fue visto prisionero y siendo conducido al norte!

The corresponding English source was identified as:

> Sir, our scouts report that Baran was seen captured and carried away further north!

### Investigation

The Spanish version was compared with the English source.

The meaning is understandable, but the construction `fue visto prisionero y siendo conducido` sounds literal and less natural in Spanish.

The English expression `further north` also contains a nuance of movement farther toward the north that is not fully reflected by simply using `al norte`.

### Finding

A more natural Spanish formulation could be:

> ¡Señor, nuestros exploradores informan que Baran fue capturado y llevado más al norte!

### Decision

**Localization observation — not elevated to bug.**

The existing translation communicates the intended meaning and does not introduce a clear semantic error. The issue concerns naturalness and translation style.

---

## L10N-OBS-004 — "Turnos finalizados pronto"

### Context

The victory summary displayed:

> Turnos finalizados pronto: 4

The scenario was completed on turn **14/18**, leaving four unused turns.

### Investigation

The value was compared with the scenario turn counter and confirmed to correspond to the four turns that were not used before achieving victory.

The wording was then reviewed from a Spanish UX perspective.

### Finding

The current wording is understandable but somewhat unnatural.

Possible alternatives include:

- `Turnos no utilizados: 4`
- `Turnos terminados antes de tiempo: 4`
- `Turnos restantes: 4`

`Turnos restantes` is more immediately understandable, although it may introduce a slightly different interpretation depending on context.

### Decision

**Localization / UX observation — not elevated to bug.**

The information is accurate and understandable. The observation concerns wording clarity rather than incorrect localization.

---

## L10N-OBS-005 — "Bonificación por finalizar pronto"

### Context

The victory summary also displayed:

> Bonificación por finalizar pronto: 16 por turno

### Investigation

The wording was reviewed together with the related `Turnos finalizados pronto` label.

The intended meaning can be understood as the bonus associated with completing the scenario before using all available turns.

### Finding

The phrase is understandable but could potentially be made more natural or explicit in Spanish.

### Decision

**Localization observation — not elevated to bug.**

No incorrect information or blocking ambiguity was identified.

---

## L10N-OBS-006 — Truncated Help navigation labels

### Context

Several entries in the Help navigation panel were displayed in shortened form, for example:

> Torreón de castil...

> Ruina de castillo...

> Castillo humano ...

> Tienda de camp...

### Investigation

The entries were selected individually to determine whether the complete names remained accessible.

The complete name of the selected entry is displayed in the main content area.

### Finding

The truncation is controlled and does not permanently hide the content.

However, several entries share similar prefixes, which can make navigation less immediately distinguishable.

### Decision

**Localization / UX observation — not elevated to bug.**

The full content remains accessible. The observation concerns navigation clarity rather than a confirmed localization defect.

---

## L10N-OBS-007 — Regional wording: "echaremos en falta"

### Context

The expression:

> echaremos en falta

was observed during the exploratory localization review.

### Investigation

The expression is grammatically valid Spanish and is naturally used in some Spanish-speaking regions.

Its frequency and naturalness vary between Spain and different Latin American varieties.

The target regional variant for this localization was not established sufficiently to classify the expression as incorrect.

### Finding

The expression is valid Spanish, although its regional naturalness may vary.

### Decision

**Localization observation — not elevated to bug.**

Without a defined target locale or style guide requiring a different regional expression, there is insufficient evidence to classify this as a defect.

---

## L10N-OBS-008 — "Cualquiera de los bandos"

### Context

The phrase:

> cualquiera de los bandos

was reviewed during the Tutorial localization.

### Investigation

The wording was compared with the intended meaning of the English expression `either side`.

The Spanish phrase is understandable and grammatically valid.

### Finding

Alternative wording could potentially be more direct depending on the intended nuance, but no clear semantic error was established.

### Decision

**Localization observation — not elevated to bug.**

The phrase communicates the intended meaning and no objective localization error was confirmed.

---

## Decision Criteria

An observation was kept separate from confirmed defects when:

- the meaning remained correct;
- the wording was understandable;
- the issue depended on regional preference or style;
- the English source did not provide sufficient evidence of an error;
- the behavior was functionally correct;
- or the proposed change represented an improvement rather than a correction.

These observations demonstrate areas where the localization could potentially be refined without claiming that the existing text is defective.
