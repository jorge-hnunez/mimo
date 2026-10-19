---
name: mimo-user-story
description: Write or refine a user story for the Mimo dog-adoption app in English, using the US-XX title, story statement and Gherkin acceptance criteria format used on the Mimo GitHub board.
---

# Mimo user story

Use this when asked to write, refine or split a user story for Mimo.

## Before writing
- Read CLAUDE.md for the domain rules and stack.
- List existing issues (`gh issue list --state all --limit 200`) so the story is not a duplicate, and use the next free US number.

## Format

Issue title: `US-XX <Short descriptive title>` (readable on its own, e.g. "US-13 Log in with email and password").

Issue body:

````markdown
## User story
As a <adopter | foundation | administrator | developer>, I want <goal>, so that <benefit>.

**Epic:** EX · <Epic name>
**Screens:** <Screen name (ID)>

## Acceptance criteria
```gherkin
Feature: <feature>

  Scenario: <happy path>
    Given ...
    When ...
    Then ...

  Scenario: <validation or edge case>
    ...
```

## Out of scope
- (optional)

## Technical notes
- (optional)
````

## Rules
- Everything in English.
- 2 to 5 scenarios: happy path first, then validation, empty, error and permission cases.
- Use concrete values from the domain rules in CLAUDE.md.
- Use Scenario Outline with Examples when the same rule applies to several inputs.
- Steps describe behavior the user can observe, not implementation.
- No labels, assignees or dependencies. On the board, set only Status (Todo) and Epic.

## Epics
E0 Technical Foundation · E1 Access and Account · E2 Adopter Profile · E3 Dog Discovery · E4 Adopter Requests · E5 Foundation Onboarding and Profile · E6 Dog Management · E7 Foundation Requests and Adoption · E8 Adopter Follow-up · E9 Foundation Follow-up · E10 Notifications · E11 Legal and Release
