# Psychiatry Mnemonic Reviewer

**Final release candidate — Pass 10: Final Polish, QA & Release Documentation**

A mobile-first, offline-first psychiatry mnemonic study app built around a **241-entry source-faithful mnemonic database**.

## Current content

- **241 canonical mnemonic entries**
- **5 source pages**
- Source-page counts: **58 / 51 / 69 / 26 / 37**
- Search across mnemonic, heading, expansion, and category
- Filter by source page and topic
- Entry detail pages with previous/next navigation
- Flashcards with Easy / Medium / Hard spaced repetition
- Due, new, hard, random, and all-card review sessions
- Active-recall quizzes with missed-question retry
- Educator printable two-column study sheets
- Local progress/review dashboard
- Light/dark mode
- Responsive iPhone/iPad/desktop layout
- PWA/service-worker offline support

## Source policy

The canonical content layer preserves the source wording, headings, expansions, page placement, and audit-status fields from the consolidated mnemonic database.

**This app is source-faithful, not clinically fact-checked.** The mnemonic text has not been silently corrected, supplemented, reconciled, or replaced with general psychiatry knowledge. Clinical validation is intentionally a separate future pass.

## Learner data

Flashcard review metadata and quiz statistics are stored locally in the browser and are kept separate from the canonical source content. Resetting learner progress does not modify the source mnemonic database.

## Offline / PWA behavior

The app is designed for GitHub Pages and caches its application shell and source data through a service worker after the first successful load. The deployment should be served over **HTTPS** for service-worker installation.

## Release QA — Pass 10

### Automated checks completed

- [x] Canonical database contains exactly **241 entries**.
- [x] Source-page counts remain **58 / 51 / 69 / 26 / 37**.
- [x] Required source-faithful content is present.
- [x] Easy / Medium / Hard spaced-repetition logic is present.
- [x] LocalStorage review and quiz persistence is present.
- [x] Quiz modes and missed-question queue are present.
- [x] Printable two-column Study Sheets are present.
- [x] Progress dashboard and reset behavior are present.
- [x] PWA manifest uses relative `start_url` and `scope` suitable for GitHub Pages.
- [x] Service-worker registration and offline fallback are present.
- [x] Required PWA/icon assets are present.
- [x] HTML asset references are relative and resolve within the release package.
- [x] `node --check app.js` passed.
- [x] `node --check sw.js` passed.
- [x] ZIP/package integrity passed.
- [x] About screen and README were updated for the final feature set.

### Manual deployment QA still required

The following cannot honestly be marked complete by static/package checks alone:

1. Deploy the release to the intended **HTTPS GitHub Pages** URL.
2. Open the app on a real iPhone/iPad or desktop browser.
3. Allow the service worker to install and finish caching.
4. Confirm major navigation paths work normally.
5. Confirm flashcards, ratings, quiz, Study Sheets, and progress work after refresh.
6. Disable network access.
7. Reload the deployed app.
8. Confirm the application shell and mnemonic database remain usable offline.
9. Test portrait and landscape layouts, dark/light mode, touch targets, scrolling, and flashcard gestures on the intended devices.
10. Re-enable network and confirm normal operation resumes.

**Release status:** code/package QA complete; real-device GitHub Pages offline QA remains the final external test.

## Roadmap / pass history

1. Foundation — complete
2. Flashcards + spaced repetition — complete
3. Quiz / active recall — complete
4. Educator printable two-column study sheets — complete
5. Progress and review dashboard — complete
6. Pixel-art visual identity and app assets — complete
7. Dark/light visual polish — complete
8. Mobile/iPhone/iPad polish — complete
9. PWA/offline/GitHub Pages hardening — complete
10. Final polish, QA, and release documentation — complete

## Attribution

App created by Isabella Navarro, MD.  
Latest version October 2026.  
isaymotion@gmail.com

## Pass 11 — Hearted Custom Deck

Pass 11 adds a learner-owned heart/favorites layer without changing the canonical source database.

### Hearted cards
- Every flashcard has a heart control (♡ / ♥).
- Every quiz item has the same heart control.
- Heart state is shared between flashcards and quiz questions.
- Heart state persists locally in `localStorage` under `pmr-hearts-v1`.
- Hearts are independent of Easy / Medium / Hard spaced-repetition ratings.
- Reset learner progress also clears the Hearted deck.

### Hearted study modes
- **♥ Hearted** — review the complete custom deck.
- **♥ Hearted + Due** — review only hearted cards currently due.
- **♥ Hearted + Hard** — review only hearted cards rated Hard.
- Quiz includes **♥ Hearted Questions** as a dedicated quiz mode.

### Source integrity
Heart state is learner metadata only. It does not modify the 241 source-faithful mnemonic records, their wording, source pages, headings, expansions, or audit fields.

### Additional Pass 11 QA fix
The final-QA JavaScript referenced `buildDeck()` from `startFlash()` but did not contain that function. Pass 11 restores the deck-building function and explicitly supports due, new, hard, random/all, and Hearted filters.


## Pass 13 — Hearted UX Polish

- Hearted Deck is available directly from Home / Quick Start.
- Progress / Review provides Hearted, Hearted + Due, and Hearted + Hard entry points.
- Flashcard sessions expose quick deck-switch controls for Hearted, Due, and Random study.
- Keyboard users can press **H** while studying a flashcard to toggle its heart.
- Heart state remains shared and persistent across flashcards and quiz questions.
- The source-faithful 241-entry database remains unchanged.


## Pass 13 — Mobile/PWA hardening
- Hardened iPhone/iPad viewport and safe-area handling.
- Added 44px minimum touch targets and touch-action optimization.
- Added dynamic/small viewport handling for mobile Safari.
- Preserved reduced-motion behavior and strengthened mobile quiz/flashcard layouts.
- Bumped service-worker cache to `pmr-pass13-v1`.
- Updated visible release version to Pass 13.

## Final real-device validation
The remaining deployment-specific check is to open the GitHub Pages site over HTTPS, allow the service worker to finish installing, then disable network and reload. This confirms the real hosting origin, browser cache, and offline navigation behavior together.
