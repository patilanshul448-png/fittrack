FITTRACK NEXUS — YOUR PERSONAL LIFE SYSTEM
Complete rebranded PWA release · 20 November 2026

WHAT'S INCLUDED
- Existing FitTrack application, with its existing features and layouts retained.
- Rebranded FitTrack Nexus name, browser metadata and new app icons.
- Existing local-first fitness, nutrition, sleep, journal, calendar and progress features.
- Home, Planner, Study, Wellness and More destinations, plus Finance and Notes modules already present in the supplied app.
- Offline-first PWA shell and service worker.
- Supabase schema and bootstrap-owner Edge Function scaffold in the correct folder structure.
- Existing localStorage key preserved: fittrack_standalone_v1.

IMPORTANT: FRONTEND VS BACKEND
GitHub Pages serves the static frontend (index.html, manifest.webmanifest, icons and sw.js). It does not run Supabase Edge Functions or execute Deno TypeScript. Supabase is a separate hosted backend. The frontend's local-first features remain usable without Supabase; backend features described as future/configuration-dependent are not activated merely by uploading this repository.

GITHUB REPOSITORY LAYOUT
Upload the CONTENTS of this folder to the ROOT of the new GitHub repository. Do not upload the outer ZIP folder as an extra nesting level.

index.html
manifest.webmanifest
sw.js
icon-192.png
icon-512.png
icon-512-maskable.png
supabase/schema.sql
supabase/functions/bootstrap-owner/index.ts

SUPABASE SETUP
1. Create a Supabase project.
2. In the Supabase SQL Editor, review and run supabase/schema.sql.
3. Deploy supabase/functions/bootstrap-owner as an Edge Function using the Supabase CLI or supported deployment workflow.
4. Configure required server-side secrets in Supabase, not in this repository: SUPABASE_URL, SUPABASE_SERVICE_ROLE_KEY and FITTRACK_OWNER_BOOTSTRAP_SECRET.
5. Never commit service-role keys, bootstrap secrets, OAuth client secrets or private credentials to GitHub or browser JavaScript.
6. Review the Edge Function and database row-level security policies before using real accounts or private data.

GITHUB PAGES
1. Create a new repository named: FitTrack-Nexus (or your chosen repository slug).
2. Upload the contents of this folder to the repository root.
3. Open Settings → Pages. Choose Deploy from a branch, branch main, folder /(root), then Save.
4. Wait for the Pages deployment to finish, then open the published HTTPS URL.
5. Test the website in a normal browser before installing the PWA.

DATA PRESERVATION
- The existing localStorage key fittrack_standalone_v1 is intentionally unchanged.
- The app's existing local records remain in the browser profile where they were created; GitHub or a new repository does not transfer them.
- Export a backup from the existing app before upgrading or moving devices.
- Do not clear browser/site storage or uninstall the old app until the new release is tested and a backup is safely stored.
- The service worker cache is separate from localStorage records. This release uses a new cache namespace, fittrack-nexus-v1.

OFFLINE AND UPDATES
- Visit the HTTPS Pages URL once while online so the app shell can be cached.
- The service worker uses a network-first strategy for page navigation and cached assets as an offline fallback.
- On a new release, increment CACHE_NAME in sw.js (for example fittrack-nexus-v2).
- Test an update in Chrome before replacing the installed app. Never delete localStorage to solve a cache issue.

TEST CHECKLIST
- Confirm the deployed site shows FitTrack Nexus and the new icon.
- Test the main navigation and existing fitness/wellness tools.
- Export a backup and confirm the file downloads.
- Test offline launch after one successful online visit.
- Test on Android Chrome and desktop Chrome.
- Configure and security-review Supabase separately before enabling backend account features.

SCOPE NOTE
This is a rebrand and packaging update, not a redesign or a claim that all future AI, account, cloud-sync, payment, passkey or multi-user features are live. Existing application behavior is retained; Supabase-dependent capabilities require separate implementation, deployment and security review.
