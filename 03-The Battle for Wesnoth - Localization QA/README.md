# The Battle for Wesnoth — Localization QA

Personal QA project focused on evaluating the Spanish localization of **The Battle for Wesnoth**, an open-source turn-based tactical strategy game.

## Project Objective

Evaluate the quality of the English → Spanish localization of the **Tutorial Campaign**, with emphasis on linguistic accuracy, terminology consistency, contextual correctness, and UI presentation.

The project combines exploratory testing in English and Spanish with structured localization testing.

## Scope

### In Scope

- Tutorial Campaign
- English → Spanish localization
- Dialogues and narrative text
- Tutorial instructions
- Objectives and messages
- Relevant UI elements
- Unit, character, faction, and location terminology
- Translation accuracy
- Grammar and spelling
- Terminology consistency
- Contextual correctness
- Spanish-specific UI issues
- Text truncation and overflow
- Character and punctuation issues
- Consistency of player address and register

### Out of Scope

- Random gameplay tips displayed at startup
- Other campaigns
- Multiplayer
- Map editor
- User-made content and add-ons
- Other platforms
- Other target languages

## Testing Approach

The project will be performed in several stages:

1. **Exploratory testing in English**
   - Understand the Tutorial flow.
   - Identify scenarios, mechanics, characters, units, instructions, and relevant UI.
   - Establish a practical reference for expected behavior.

2. **Exploratory testing in Spanish**
   - Repeat the relevant Tutorial flow.
   - Identify visible differences and localization issues.

3. **English → Spanish comparison**
   - Compare original and localized text in context.
   - Evaluate meaning, terminology, grammar, and consistency.

4. **UI Localization testing**
   - Check text visibility, truncation, overflow, layout, characters, and readability.

5. **Bug validation and reporting**
   - Reproduce identified issues.
   - Document actual and expected results.
   - Provide the English source text and Spanish translation when relevant.
   - Attach evidence.

## Testing Artifacts

- [Project Scope](01-scope.md)
- [Test Strategy](02-test-strategy.md)
- [Exploratory Testing Notes](03-exploratory-testing.md)
- [Localization Checklist](04-localization-checklist.md)
- [Test Cases](05-test-cases.md)
- [Bug Report Template](06-bug-report-template.md)
- [Terminology Glossary](07-glossary.md)


## Testing Status

### Completed
- Tutorial Campaign — exploratory localization testing
- Spanish localization review
- English → Spanish comparison
- Player-address consistency review
- Main-menu tips review
- Terminology validation
- Investigated and rejected localization candidates

### Current Findings
- 3 confirmed localization defects
- Multiple investigated candidates rejected after validation
- Additional campaign testing in progress
