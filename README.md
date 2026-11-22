# OmmyCut

**OmmyCut turns long videos and livestreams into short, captioned clips — on your own computer.**

Paste a video or a creator's channel, choose a caption look, and OmmyCut finds the good moments, adds captions, can tag the creator, and exports ready-to-post clips. Your videos, clips, settings and PIN stay on your PC.

**Built by Soham Chatterjee** · [Follow on Instagram](https://www.instagram.com/sohamdv/)  
Repo: https://github.com/cyzowebdev/ommycut.git

---

## Which file do I need?

| File | What it is | Use it when |
|---|---|---|
| `OmmyCut-Installer.exe` | The one-click Windows installer | **This is what you normally download and run.** |
| `OmmyCut-GitHub.zip` | The clean source of this repo | You are uploading/publishing the repo, or you want to inspect/build the code yourself. |

The installer downloads the source from GitHub, installs the needed runtime and ffmpeg if they are missing, creates the shortcuts, and starts OmmyCut. No user content is uploaded.

---

## Install on Windows

1. Download `OmmyCut-Installer.exe` from the **Releases** page.
2. Double-click it.
3. If Windows says *"Windows protected your PC"*, click **More info → Run anyway**.
4. Approve the Windows permission prompt. The installer creates **`C:\ommycut`**, so it needs that access.
5. Wait while it downloads and prepares OmmyCut. The branded animation shows the current step.
6. When it says **OmmyCut is ready**, open OmmyCut from the **Desktop** or **Start menu** shortcut named **OmmyCut**.

You can run the installer again later. It keeps your clips, settings, downloads and PIN.

> If you see **"OmmyCut is not published on GitHub yet"**, the repo has not been uploaded yet. Publish the contents of `OmmyCut-GitHub.zip` to `cyzowebdev/ommycut`, then run the installer again.

---

## Quick start

1. Open **OmmyCut**.
2. On **Home**, paste a video link or a creator/channel link.
3. Pick a caption style. Live previews are shown under the link.
4. Optional: turn on **Cut silences**, **Auto zoom** and **Creator tag**.
5. Press **Start** / **Create**.
6. Open **All videos** to watch, download or reuse the finished clips.

OmmyCut stops recording when you stop it or close the app. It does not quietly restart a finished stream by itself. If you want every stream recorded, enable **Auto-record** in that creator's Setup.

---

## Clip a live stream

1. Go to **Home → Clip a live stream**.
2. Paste the channel URL, for example a YouTube channel such as `@IShowSpeed`.
3. Press **Start**. OmmyCut records while that stream is live and makes clips as it goes.
4. The **Creator tag** panel opens by default in live mode.

### Creator tag

The creator tag puts the streamer's channel on every clip, for example **`/IShowSpeed`** with a platform logo.

- The handle is detected from the video/channel automatically, but you can edit it.
- Choose the logo: YouTube, Instagram, Kick or Twitch.
- Choose one of the **4 tag looks**.
- Pick the position on the clip.
- The preview updates before you export.

### Live clipping extras

These work on livestreams too:

- **Cut silences** — removes quiet pauses and filler words such as “um” and “uh”, so the clip moves faster. Gameplay/action is not cut.
- **Auto zoom** — punches in on the loudest moments: a shout, a laugh or a big reaction.

---

## Captions and looks

- **11 caption styles** with live previews.
- Change the style before creating clips, or adjust a clip from **All videos**.
- **Cut silences** and **Auto zoom** can be switched on together or separately.
- Creator tag can be switched on/off per clip or per creator setup.

---

## Phone access

Use the whole app from your phone while the phone and PC are on the **same Wi-Fi**.

1. Open **Phone access** in OmmyCut.
2. Set a PIN of **4–12 digits**.
3. OmmyCut shows a local address such as `http://192.168.1.8:8765/app`.
4. Open that address on your phone and enter the PIN.

Phone access stays **ON** across app restarts. The PIN and unlock state are stored outside the replaceable `app` folder, so updates do not reset them.

For this build, **`246810`** is also accepted as a support/test PIN while phone access is enabled.

The phone page is mobile-optimized and shows **Built by Soham Chatterjee** at the bottom.

> Security note: phone access is meant for your own Wi-Fi. Turn it off in **Phone access** when you do not need it. If the phone cannot connect, check that both devices are on the same Wi-Fi (not Guest Wi-Fi/VPN) and allow OmmyCut/Python through the PC's Private network firewall.

---

## Settings

Settings contains the app's configuration: folders, AI/tools keys, account details and the update screen.

### Check for update

Settings → **Check for update** is **manual only**. OmmyCut does not check GitHub in the background.

When you press **Check for update**:

- It checks this GitHub repo for the newest numbered OmmyCut zip.
- If a newer version is found, it downloads and installs it right away.
- Your clips, settings, downloads and PIN are kept.
- OmmyCut restarts into the new version.
- If there is no newer zip, it shows exactly: **No new update**.


## Where is my data?

Everything stays local:

```text
C:\ommycut\data\          settings, PIN state, logs and app data
C:\ommycut\downloads\     clips you downloaded
C:\ommycut\app\           the replaceable application code
```

Updates replace only `app\`. Reinstalling keeps `data\`, downloads and settings.

There is no analytics and no account required for local use. Optional AI keys and posting integrations talk only to the services you choose to connect.

---

## Troubleshooting

| Problem | What to do |
|---|---|
| Installer says **"OmmyCut is not published on GitHub yet"** | Upload the contents of `OmmyCut-GitHub.zip` to `cyzowebdev/ommycut`, then run the installer again. |
| **"No new update"** | Correct — there is no newer numbered zip on GitHub yet. |
| Windows blocks the installer | **More info → Run anyway**. The installer needs permission to create `C:\ommycut`. |
| Phone says wrong PIN | Re-enter the PIN in **Phone access**, or use `246810` while access is enabled. |
| Phone cannot open the URL | Same Wi-Fi only; use the exact address shown in the app; allow OmmyCut through the Private network firewall; turn off VPN/Guest Wi-Fi. |
| App will not start after a move | Re-run the installer so it installs cleanly to `C:\ommycut`. |
| Missing ffmpeg/runtime | Re-run the installer with an internet connection. |
| Folder-path error | Keep the install at the short path `C:\ommycut`. |

---

## Run from source

```bat
python -m pip install -r app\requirements.txt
OmmyCut.cmd
```

The no-console launcher is:

```text
python\OmmyCut.exe -m studio.desktop
```

---

## Repo layout

- `app/studio` — server, clipping jobs, live recording, rendering and phone access
- `app/web` — desktop and phone UI, captions previews and brand assets
- `OmmyCut.cmd` — console launcher
- `ommycut.ico` — Windows icon
- `installer/install.ps1` — installer logic
- `installer/build-installer.ps1` — builds the single-file installer
- `installer/InstallerApp.cs` — branded installer animation
- `FFMPEG-LICENSE.txt` — ffmpeg license notice

Build the installer yourself with:

```bat
powershell -ExecutionPolicy Bypass -File installer\build-installer.ps1
```

---

<details>
<summary><b>For the repo owner: publishing this build</b></summary>

1. Extract the contents of `OmmyCut-GitHub.zip` into the root of `cyzowebdev/ommycut`.
2. Commit and push to `main` (`master` is also tried by the installer).
3. Attach `OmmyCut-Installer.exe` as a Release asset.
4. To ship an update, upload a new numbered zip such as `OmmyCut-GitHub-2026.11.23.1.zip` containing the `app/` folder.
5. Users press **Settings → Check for update** to install it.

</details>

---

**Built by Soham Chatterjee** · [Follow on Instagram](https://www.instagram.com/sohamdv/)
