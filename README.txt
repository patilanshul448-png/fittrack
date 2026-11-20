FITTRACK PWA — FREE INSTALLABLE WEB APP PACKAGE

FILES
- index.html: FitTrack application
- manifest.webmanifest: install metadata and app icon references
- sw.js: offline app-shell cache
- icon-*.png: app icons

IMPORTANT
A Progressive Web App must be opened from HTTPS or localhost. Opening index.html directly from the Downloads folder (file://) will still run the app, but browsers do not allow service-worker registration or full PWA installation from file://.

FREE ANDROID INSTALL (HOSTED)
1. Keep all files in this folder together.
2. Publish this folder using a free static HTTPS host, for example GitHub Pages.
3. Open the published HTTPS address in Chrome on Android.
4. Visit once while online so the service worker can cache the app shell.
5. Use Chrome menu (⋮) > Install app or Add to Home screen.

LOCAL DATA
FitTrack keeps its existing localStorage key: fittrack_standalone_v1. Existing data is not uploaded. Browser storage may be isolated between the old file:// copy and the hosted PWA. Before switching, export a FitTrack backup from the old version and import it into the PWA copy. Keep exporting backups regularly.

NO PAID SERVICE IS REQUIRED BY THIS PACKAGE. Hosting provider terms and free-tier limits can change. Voice input and notifications depend on browser support and permissions. The service worker caches the app shell, not external services.


UPDATING THE APP
- To publish a new version, replace index.html and sw.js in the GitHub repository with the updated files and commit the changes.
- The service-worker cache version is bumped for this release so the new app shell can be downloaded.
- Reopen the installed app while online. If the old screen remains, close it fully and reopen; the service worker may need a moment to activate.
- Existing local records use the same localStorage key. Do not change it when updating.
