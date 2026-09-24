# AOD Theme Manager (HyperOS)

Pick 20 Always-On Display themes from a visual preview grid, and get back a
ready-to-restore `.bak` backup with those themes applied.

This is a small local website: it runs on your own computer or phone and
opens in your browser. It never uploads anything anywhere.



## Requirements

- **Python 3.8+**
- The `flask` package (installed in one command below)

---

## Setup — Windows

1. Install Python from [python.org](https://www.python.org/downloads/) if
   you don't already have it. During install, tick **"Add Python to PATH"**.
2. Download the Latest "AOD Theme Manager.zip" as well as the "Always-on display(com.miui.aod).bak" and "descript.xml" files
3. Unzip this AOD Theme Manager anywhere (e.g. your Desktop).
4. Open **Command Prompt** or **PowerShell** in that folder (Shift + Right-click
   inside the folder → "Open PowerShell window here", or type `cd` to it).
5. Install Flask:
   ```
   pip install flask
   ```
6. Run the app:
   ```
   python app.py
   ```
7. Open your browser and go to:
   ```
   http://127.0.0.1:5000
   ```
8. Click theme previews to select up to 20, then click **Generate Backup**,
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
   
3. Install Flask:
   ```
   pip install flask
   ```
4. Install wget:
   ```
   pkg install python git wget unzip
   ```
5. Download the app:
   
   ```
   wget https://github.com/haadi76/AOD-Theme-Manager-HyperOS-/releases/latest/download/aod_theme_manager.zip
   ```
6. Unzip the app
   ```
   unzip aod_theme_manager.zip
   ```
7.run the app
   ```
   python app.py
   ```
8. Open your phone's browser (Chrome, etc.) and go to:
   ```
   http://127.0.0.1:5000
   ```
9. Select up to 20 themes and generate as above. The finished file is saved
   inside Termux's own storage, at `output/custom_aod_backup.bak` — copy it
   out to shared storage so you can restore it via Settings:
   ```
   cp output/custom_aod_backup.bak /sdcard/Download/
   ```

---

## Restoring the backup on your phone
1.If its your first time restoring through the aod theme manager, first restore the provided "Always-on display(com.miui.aod).bak" and descript.xml file in folder 20240405. 

If the folder doesn't exist, create a new folder in AllBackup named  "20240405"
Open **Settings → About phone → Backup & restore → phone → restore and then select the one file named february 19 10:42 am** and then restore.
    
2. Copy the downloaded custom_aod_backup.bak file to your phone (in case of windows and internal storage/MIUI/backup/AllBackup/20240405. Rename the file to "Always-on display(com.miui.aod).bak" exactly without quotation marks. Also copy the descript.xml file inside the same folder.

If the folder doesn't exist, create a new folder in AllBackup named  "20240405".

4. Open **Settings → About phone → Backup & restore → phone → restore and then select the one file named february 19 10:42 am** and then restore.

5. Open the AOD theme picker — your 20 new themes should appear in place of
   the originals.

---

## Notes

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
- **Backup doesn't restore correctly**: 
- Check that the backup file is named correctly if it fails to restore.
- If the backup restores but the selected themes don't appear, then restore the orignal.bak file provided and then try again.
- if the themes still don't appear in the AOD gallery, then report the issue.
  
