# FitTrack — Initial Technical Audit

Audit date: 20 November 2026

## Existing baseline inspected

- Existing installable PWA package: `FitTrack-PWA-Free.zip`
- App entry point: `index.html` (146,505 characters)
- Offline worker: `sw.js`
- Manifest and three PNG app icons are present.
- Existing local data key: `fittrack_standalone_v1`
- Existing top-level app sections: dashboard, planner, workout, nutrition, mobility, facecare, sleep, progress, journal, calendar, settings.
- Current service-worker cache: `fittrack-pwa-v2`
- Duplicate HTML IDs detected by a simple static scan: 0
- Inline JavaScript blocks: 1
- JavaScript syntax check: passed with Node.js `--check`.

## Current architecture observed

- Single-page HTML/CSS/JavaScript PWA.
- Local-first data stored in browser `localStorage`.
- Existing service worker caches the app shell for offline launch.
- The README explicitly states that existing local data is not uploaded.
- Existing app sections include Dashboard, Planner, Workout, Nutrition, Mobility, Face & senses, Sleep, Progress, Journal, Calendar and Settings.

## Important gaps relative to the new master blueprint

These are not assumed to exist just because they are in the plan:

1. Secure account registration, login, password recovery and sessions.
2. Multi-device cloud database and conflict-safe synchronization.
3. Free-trial lifecycle, plan entitlements and paid plan access control.
4. Nexus AI, Apex Jarvis and separate Owner AI services.
5. Owner-only control centre with strict role-based permissions and audit logs.
6. Workout public communities, private groups, moderation and consistency leaderboard.
7. Future QR payment workflow and owner-configurable prices.
8. Full desktop-responsive five-tab information architecture.
9. Server-side Google/web verification for current external facts.
10. Production monitoring, automated tests and release pipeline.

## Data safety constraints

- Do not rename or discard `fittrack_standalone_v1` during the transition.
- Before any schema migration, export a backup and test import/restore.
- Add versioned migrations and preserve unknown fields where possible.
- Never let a new service worker delete user data; cache cleanup must only affect app-shell caches.
- Do not place AI provider keys, database service-role keys, or payment secrets in frontend HTML.
- Never let the Owner role read users' private nutrition, health, journal, study or finance records by default.

## Development sequence

### Phase 1 — Foundation and safe migration
- Establish a versioned data layer and migration tests.
- Build account/session architecture and role/plan entitlements.
- Define offline queue, sync states, conflict resolution and backup/restore.
- Preserve the existing local data format through an explicit migration adapter.

### Phase 2 — Core product shell
- Reorganize the interface into Home, Planner, Study, Wellness and More.
- Add profile, account, appearance, privacy, notification and device settings.
- Implement Free trial state and plan comparison UI with placeholder prices.

### Phase 3 — Core modules
- Planner, Study, Nutrition, Fitness, Sleep & Recovery, Daily Health.
- Finance and Notes & Knowledge.
- Insights and history.
- Workout community with privacy-first defaults and moderation.

### Phase 4 — AI services
- Nexus advanced AI (no Jarvis).
- Apex Jarvis (voice/text, user-authorized FitTrack actions, confirmations).
- Owner AI (limited authority, queued approvals, full audit trail).
- Owner's separate My Fitness section and advanced personal fitness AI.
- Grounded web verification with citations and explicit uncertainty.

### Phase 5 — Plans, payments and release
- Free trial: 3 months per account; after expiry, user must choose a paid plan to continue.
- Paid editions: Core, Nexus, Apex; prices remain placeholders until configured.
- Payment collection remains disabled until owner configures and approves the future QR workflow.
- Security, accessibility, performance, offline, sync and device testing.
- Release a single replacement ZIP only after regression checks pass.

## Confirmed product rules

- Free: 3-month trial, basic features, no AI/Jarvis; after expiry, require paid-plan selection.
- Core: paid, essential features, no AI/Jarvis.
- Nexus: paid, advanced AI features, no Jarvis.
- Apex: paid, advanced AI plus Jarvis.
- Jarvis is also available in the private Owner account.
- Owner account has two main sections only: Owner and My Fitness.
- Owner AI can do predefined low-risk tasks independently; important decisions require owner approval.
- Owner AI must identify itself honestly and keep an auditable record of actions.
- Owner controls must not expose users' private personal records or passwords.
- Workout community includes public communities and private friend groups; points reward consistency, not intensity.
- QR payments and actual prices are deferred; show price placeholders for now.
- Smartwatch integration is paused and excluded from the current scope.
- UI should remain clean, minimal and responsive.
