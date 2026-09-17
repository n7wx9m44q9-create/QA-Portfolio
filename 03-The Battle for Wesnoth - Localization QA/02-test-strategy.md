# Test Strategy

## 1. Testing Objectives

The primary objective is to evaluate the Spanish localization of the Tutorial Campaign against the English source version.

The testing will focus on:

- Translation accuracy
- Linguistic quality
- Terminology consistency
- Contextual correctness
- UI localization
- Reproducibility of localization defects

## 2. Testing Approach

Testing will be performed in sequential stages.

### Phase 1 — English Exploratory Testing

The Tutorial will first be explored in English.

The objective is not to perform a complete functional test, but to understand:

- Tutorial structure
- Scenario flow
- Characters
- Units
- Gameplay mechanics introduced
- Objectives
- Instructions
- Dialogues
- Relevant UI elements
- Expected player actions
- Important state changes

The observations will provide contextual information for the later localization comparison.

### Phase 2 — Spanish Exploratory Testing

The relevant Tutorial flow will then be repeated in Spanish.

The objective is to identify:

- Missing translations
- Unexpected English text
- Meaning changes
- Inconsistent terminology
- Linguistic issues
- Contextual issues
- UI localization problems

### Phase 3 — English → Spanish Comparison

Relevant texts will be compared directly with their English source.

The comparison will consider:

- Meaning
- Context
- Terminology
- Grammar
- Register
- Player address
- Names
- Instructions
- UI terminology

### Phase 4 — UI Localization Testing

Spanish text will be evaluated visually for:

- Truncation
- Overflow
- Overlapping elements
- Incorrect line breaks
- Missing characters
- Incorrect special characters
- Text visibility
- Button layout
- Dialog layout
- Readability

### Phase 5 — Defect Validation

Potential issues will be validated before reporting.

Each report should contain enough information to reproduce and understand the problem.

## 3. Language Switching Exploration

The behavior of language switching will be explored rather than assumed.

The following will be investigated:

- Whether the language can be changed during a session.
- Whether changing English → Spanish updates the current interface.
- Whether changing Spanish → English updates the current interface.
- Whether previously loaded text remains in the previous language.
- Whether language switching affects gameplay or progress.
- Whether the selected language persists after restarting the application.

These observations may result in additional test cases if relevant.

## 4. Localization Defect Categories

Potential defects will be classified as:

### Translation

- Incorrect translation
- Meaning changed
- Missing information
- Added information
- Incorrect interpretation

### Linguistic

- Grammar
- Spelling
- Punctuation
- Agreement
- Register
- Player address

### Consistency

- Terminology inconsistency
- Name inconsistency
- Inconsistent translation of the same concept
- Inconsistent UI terminology

### Context

- Translation does not fit the situation
- Incorrect reference
- Ambiguous instruction
- Incorrect gameplay terminology

### UI Localization

- Truncation
- Overflow
- Text overlap
- Incorrect line breaks
- Character rendering problems
- Layout problems

## 5. Evidence

Evidence may include:

- Screenshots
- English source text
- Spanish localized text
- Scenario information
- Reproduction steps
- Relevant contextual information

## 6. Defect Validation Criteria

A potential issue should be validated before being reported.

The issue should preferably:

- Be objectively identifiable.
- Have a reproducible or clearly observable behavior.
- Have sufficient context.
- Have an identifiable expected result.
- Be supported by evidence when appropriate.

Personal stylistic preference alone should not be treated as a localization defect.
