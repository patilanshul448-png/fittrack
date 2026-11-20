# FitTrack — Master Product & Technical Blueprint

**Product:** FitTrack — Your Personal Life System  
**Status:** Development started; existing PWA baseline audited  
**Date:** 20 November 2026

## Product structure

Five primary destinations:
1. Home
2. Planner
3. Study
4. Wellness
5. More

Wellness contains Nutrition, Fitness, Sleep & Recovery, and Daily Health. More contains Finance, Notes & Knowledge, Insights, account/profile, settings, and plan information.

## Editions

| Edition | Access |
|---|---|
| Free | 3-month trial per account; basic features only; no AI or Jarvis |
| Core | Paid essential edition; no AI or Jarvis |
| Nexus | Paid edition with advanced AI; no Jarvis |
| Apex | Paid edition with advanced AI and Jarvis |

At the end of the 3-month Free trial, users must select a paid plan to continue. No automatic charge. Prices are placeholders until configured. Payment collection is not being implemented now.

## AI roles

### Nexus AI
Advanced AI features such as meal photo estimates, workout suggestions and smart insights. No Jarvis persona or wake-name interaction.

### Apex Jarvis
A named voice/text assistant available only in Apex and the private Owner account. It answers using permitted FitTrack data, may research current external facts through web search, cites sources, explains uncertainty, and requests confirmation before consequential changes.

### Owner AI
Private management assistant. It may perform predefined low-risk tasks independently. Important decisions and sensitive actions require owner approval. It must identify itself as the FitTrack Owner Assistant, never impersonate the owner, and maintain an audit log.

### Owner account layout
Exactly two primary sections:
- **Owner:** administration, support enquiries, pricing controls (later), QR configuration (later), community moderation, feature/release controls, service health, AI usage and audit logs.
- **My Fitness:** owner's personal fitness, nutrition, workouts, recovery and advanced personal fitness AI.

Owner permissions do not grant access to other users' private health, nutrition, journal, study or finance records, or passwords.

## Community

Workout-only community with public communities and private groups. Sharing is opt-in. Leaderboard points reward consistency and completion of planned activity, not workout duration or intensity. Rest and recovery must not be penalized. Include blocking, reporting, moderation, privacy defaults and group exit controls.

## Data, privacy and security

- Preserve the current local data key: `fittrack_standalone_v1`.
- Use versioned migrations, backups and restore tests.
- Local-first/offline capability with queued synchronization and explicit conflict handling.
- Use a secure backend for authentication, cloud database and AI calls.
- Keep secrets server-side; never embed API keys in client HTML.
- Enforce role-based access on the server, not only by hiding UI.
- Record Owner AI actions and approvals.
- Provide account export, session management, recovery and deletion workflows.

## Performance and reliability

- Keep the mobile PWA lightweight.
- Avoid duplicate listeners, unnecessary rendering and blocking network calls.
- Lazy-load nonessential modules.
- Cache only app-shell/static assets in the service worker.
- Test offline launch, sync recovery, conflict handling, data migration and restore.
- Test Android mobile and desktop browsers.
- Do not claim zero bugs; use automated and manual regression checks.

## Deferred scope

- Smartwatch integration: paused.
- Actual prices: not decided.
- QR payment collection: not now.
- Production AI credentials/provider and cloud project: must be configured securely before live AI or account sync can work.
