# AOD Theme Manager (HyperOS)

Pick 20 Always-On Display themes from a visual preview grid, and get back a
ready-to-restore `.bak` backup with those themes applied — no manual file
swapping, no MT Manager.

This is a small local website: it runs on your own computer or phone and
opens in your browser. It never uploads anything anywhere.

---

## What's included in this download

```
aod_theme_manager/
  app.py                  <- the app (just run this)
  templates/, static/     <- the web page itself
  themes/                 <- pre-loaded theme files, ready to pick from
  original_source/apps/   <- the pristine AOD app data these get inserted into
```

You don't need to set any of this up — `themes/` and `original_source/` are
already populated. Just unzip and run.

---

## Requirements

- **Python 3.8+**
- The `flask` package (installed in one command below)

---

## Setup — Windows

1. Install Python from [python.org](https://www.python.org/downloads/) if
   you don't already have it. During install, tick **"Add Python to PATH"**.
2. Unzip this folder anywhere (e.g. your Desktop).
3. Open **Command Prompt** or **PowerShell** in that folder (Shift + Right-click
   inside the folder → "Open PowerShell window here", or type `cd` to it).
4. Install Flask:
   ```
   pip install flask
   ```
5. Run the app:
   ```
   python app.py
   ```
6. Open your browser and go to:
   ```
   http://127.0.0.1:5000
   ```
7. Click theme previews to select up to 20, then click **Generate Backup**,
   then **Download backup**. The file lands in the `output/` folder inside
   this project (also linked directly from the download button).

---

## Setup — Android (via Termux)

You'll do this entirely on your phone, no PC needed.

1. Install [Termux](https://f-droid.org/packages/com.termux/) from F-Droid
   (the Play Store version is outdated — use F-Droid).
2. Open Termux and run:
   ```
   pkg update
   pkg install python unzip
   termux-setup-storage
   ```
   Approve the storage permission popup — this lets Termux see your phone's
   normal storage (Downloads, etc.).
3. Move the downloaded zip into your phone's **Downloads** folder if it
   isn't already there, then in Termux:
   ```
   cd ~
   unzip /sdcard/Download/aod_theme_manager.zip
   cd aod_theme_manager
   ```
4. Install Flask:
   ```
   pip install flask
   ```
5. Run the app:
   ```
   python app.py
   ```
6. Open your phone's browser (Chrome, etc.) and go to:
   ```
   http://127.0.0.1:5000
   ```
7. Select up to 20 themes and generate as above. The finished file is saved
   inside Termux's own storage, at `output/custom_aod_backup.bak` — copy it
   out to shared storage so you can restore it via Settings:
   ```
   cp output/custom_aod_backup.bak /sdcard/Download/
   ```

---

## Restoring the backup on your phone

1. Copy the generated `.bak` file onto your phone (Windows users: transfer
   it over USB or however you normally move files across).
2. Open **Settings → Backup & restore** (or wherever your HyperOS version
   keeps local backup restore).
3. Restore from that file.
4. Open the AOD theme picker — your 20 new themes should appear in place of
   the originals.

---

## Notes

- Only the **first 20** theme slots get replaced; the last 6 are left
  untouched.
- Closing the terminal/Termux window stops the app. Just re-run
  `python app.py` to start it again later — your selections aren't saved
  between runs, so you'll re-pick each time.
- Everything runs locally — nothing is uploaded to the internet at any point.

## Troubleshooting

- **"python is not recognized"** (Windows): Python wasn't added to PATH
  during install — reinstall and tick that option, or use `py` instead of
  `python` in the commands above.
- **Page won't load**: make sure the terminal/Termux window is still open
  and showing `Running on http://127.0.0.1:5000` with no errors.
- **Backup doesn't restore correctly**: make sure you're using the
  unmodified `themes/` and `original_source/` folders that came with this
  download — swapping in your own without matching the expected structure
  can break the restore.
