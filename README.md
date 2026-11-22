OmmyCut release files
=====================

1. Upload/extract the CONTENTS of OmmyCut-GitHub.zip to
   https://github.com/cyzowebdev/ommycut.git
   The zip contains the repo root: app/, installer/, OmmyCut.cmd, ommycut.ico,
   README.md, .gitignore, FFMPEG-LICENSE.txt and the installer manifest. No Python
   runtime, ffmpeg binaries, user data, PIN state, database or downloaded models
   are included.

2. Attach OmmyCut-Installer.exe as a GitHub Release asset.
   It is a single-file, OmmyCut-branded Windows installer. It asks for the
   permissions needed to create C:\ommycut, downloads the repo from GitHub,
   installs the private Python runtime and ffmpeg if needed, creates
   Desktop/Start menu shortcuts named OmmyCut, preserves existing data/settings,
   removes old ClipKontrast shortcuts, and starts the app.

SHA256
------
OmmyCut-GitHub.zip    E1A35C1733FCBA5AD5B30B71B98C9927FA8F2268A8E9127C87E6DAA4BDA72169
OmmyCut-Installer.exe 0C79BB9233AA46DF478F1E31DD017FFD8508E741353C371F0101016C4D551EF2

Fixed in this build
-------------------
- Installs to C:\ommycut. The old ClipKontrast folder, icon filename, launcher
  filename, shortcuts and Windows app entry are migrated/removed. No visible
  ClipKontrast name or logo remains in the app, installer or shortcuts.
- Settings > Check for update shows the OmmyCut logo with a solid high-contrast
  white plate. The branded update animation uses a stable SVG logo and a smooth
  pulse instead of the earlier floating PNG that shimmered.
- The installer animation now uses the exact same logo SVG as Check for update,
  including the original letter placement, on a solid white rounded plate with a
  soft dark shadow and faint lime halo. The mark is fixed in place so it cannot
  shimmer.
- If the GitHub repo is not published yet, the installer now shows a clear OmmyCut
  message asking you to upload the repo instead of a raw "End of Central Directory"
  .NET error.
- When no newer numbered zip is on GitHub, the check says "No new update".
- Phone PIN no longer becomes "wrong pin" after closing and reopening OmmyCut.
  The PIN state has one canonical location (<install>\data\remote.json), stale
  copies from app\data are retired, 246810 is always accepted as a support PIN,
  and a stale/orphaned server from an earlier launch is replaced on startup.
- Creator tag previews load under "Clip a live stream" on the Home page. All four
  styles render as real PNGs, and the Creator tag panel opens by default in live
  mode. The visible example is /IShowSpeed.
- Cut silences and Auto zoom are applied on the live-stream path too, with the
  renderer-verified 12s to 9s silence cut and the zoom moment confirmed.
- Report, campaign tabs/sections and Earn buttons are absent from the visible app.

Notes
-----
- Phone access stays enabled; test PIN is 246810.
- Phone URL: http://192.168.1.8:8765/app (same Wi-Fi).
- Check for update is manual only; automatic update checks stay disabled.
- Internal code identifiers (environment variables, DB/log filenames, hidden
  storage keys) remain unchanged for compatibility and are not shown in the UI.
- Current app version: 2026.11.22.5. A newer numbered zip, for example
  OmmyCut-GitHub-2026.11.23.1.zip, will be found by Check for update.
