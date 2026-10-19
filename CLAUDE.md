# Mimo

Mimo ("Mimo | Adopción consciente") is a mobile app that helps dog rescue foundations run conscious adoptions and post-adoption follow-ups. One app, two roles chosen at sign up: **adopter** and **foundation**. The app UI is in Spanish (Mexico); code, docs, commits, issues and PRs are in English.

## Stack
- React Native with **Expo** (development builds, not Expo Go) and **EAS** Build / Submit
- **TypeScript** in strict mode
- **Firebase** through React Native Firebase: Authentication (email and password), Cloud Firestore, Cloud Storage, Crashlytics, Cloud Functions (scheduled jobs and notifications)
- Push notifications with `expo-notifications`
- Two Firebase projects: `mimo-dev` and `mimo-prod`; Firebase Emulator Suite for local work and rule tests
- Quality: ESLint (errors block, warnings do not), Prettier, Jest + React Native Testing Library, Husky + lint-staged
- CI: GitHub Actions on every PR (type check, Prettier, ESLint, Jest)

## How work is tracked
- Every user story is a GitHub issue titled `US-XX <title>` with Gherkin acceptance criteria.
- Board: GitHub Project "Mimo MVP". Only the Status field matters (Todo, In Progress, Done) plus the Epic field (E0 to E11).
- **Before starting work, check the board:** the item In Progress is the current story; the first item in Todo is the next one.
  - `gh project item-list 2 --owner jorge-hnunez --format json`
  - `gh issue view <number>`
- Branch per story: `feat/US-13-login`. PR description includes `Closes #<issue number>` so the issue moves to Done on merge.
- Commits follow Conventional Commits, e.g. `feat(auth): log in with email and password (US-13)`.
- To write a new or refined story, use the `mimo-user-story` skill.

## Domain rules (source of truth for the stories)
- **Compatibility** (informative, never blocks): rules compare questionnaire answers with dog data (space, energy, children, other pets, time alone, experience). Overall = Low if any rule is Low; Medium if two or more are Medium; otherwise High.
- **Dog states:** Draft → Available → Pending adoption → Adopted. Available dogs can be Paused (hidden from the catalog, e.g. medical treatment).
- **Request states:** Sent → In review → Approved / Rejected. Other active requests become Not selected when the adoption is registered.
- An adopter can have at most **3 active requests** (Sent, In review or Approved).
- **Follow-up plan** after delivery: 1 week, 1 month, 3, 6 and 12 months. Evidence can be sent from 3 days before to 7 days after each date; after that it is Overdue. Reminders: 3 days before and on the day.
- Foundations are verified manually by the administrator before their dogs appear in the catalog.
- Contact between adopter and foundation is through WhatsApp (no in-app chat in the MVP).

## Brand
Caramel `#EFA25E` (primary), Dark caramel `#B8692A` (text on light backgrounds, pressed states), Cream `#FDE5CD` (soft backgrounds, cards), Charcoal `#2B2B2B` (outlines, secondary text).
