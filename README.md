# Steam Client Downgrade Guide for FH6
An in-depth guide on how to downgrade your Steam client for Forza Horizon 6
## Step 1: Clear Beta (If Enrolled)

Launch Steam with `-clearbeta`, dismiss the error, then **exit Steam fully**.

Check Task Manager or System Informer — end `Steam.exe`, `steamwebhelper.exe`, `GameOverlayUI.exe`
## Step 2: Clean Cached Data

Delete contents of these folders in your Steam directory (`C:\Program Files (x86)\Steam\`)

| Folder      | Action             |
| :---------- | :----------------- |
| `package\`  | Delete everything. |
| `appcache\` | Delete everything  |

Keep everything else

## Step 3: Create the Downgrade Shortcut

1. Browse to: `C:\Program Files (x86)\Steam\Steam.exe`
    
2. Create a shortcut and name it `Downgrade`
    
3.  Right-click the shortcut → **Properties**
    
4.  In **Target**, click after the closing quote, add a space, then paste:
    


```plain
-forcesteamupdate -forcepackagedownload -overridepackageurl http://web.archive.org/web/20260611123103if_/media.steampowered.com/client -exitsteam
```

**Full Target:**

This is what it should look like

```plain
"C:\Program Files (x86)\Steam\Steam.exe" -forcesteamupdate -forcepackagedownload -overridepackageurl http://web.archive.org/web/20260611123103if_/media.steampowered.com/client -exitsteam
```

6. **OK** → Double-click to run. Steam downloads old packages and exits.
    

> **Fails?** Append `-textmode` to the end and retry.

> **Registry dialog?** Click **Repair**.

## Step 4: Block Auto-Updates

Create `steam.cfg` in `C:\Program Files (x86)\Steam\`:

1. Right-click in an **empty area** of the Steam folder
    
2. Select **New → Text Document**
    
3. A new file appears named `New Text Document.txt`
    
4. Rename it to exactly: **`steam.cfg`**
    
    - If a warning appears saying _"If you change a file name extension, the file might become unusable"_, click **Yes**
        
5. If Windows renamed it to `steam.cfg.txt` anyway, right-click it → **Rename** and remove `.txt` so it reads only `steam.cfg`

6. Right-click `steam.cfg` → **Open with → Notepad**
    
7. Type exactly this line (no extra spaces, no quotes):
    
```plain
BootStrapperInhibitAll=enable
```
8. Press **Ctrl + S** to save
    
9. Close Notepad

> **Tip:** If file extensions are hidden, Windows saves it as `steam.cfg.txt`. Enable extensions first: **View → Show → File name extensions**


## Step 5: Create the Launch Shortcut

1. Browse to: `C:\Program Files (x86)\Steam\Steam.exe`
    
2. Create another shortcut and name it: **`Steam Downgraded`** or **`Steam`**
    
3. Right-click → **Properties** → after the closing quote, add:
    

```plain
-noverifyfiles -nobootstrapupdate -skipinitialbootstrap -norepairfiles -overridepackageurl
```

**Full Target:**

```plain
"C:\Program Files (x86)\Steam\Steam.exe" -noverifyfiles -nobootstrapupdate -skipinitialbootstrap -norepairfiles -overridepackageurl
```

4. Run it. Verify at **Steam → About Steam** → should show **June 9, 2026 / 1781041600**.

**Side Note**: 
- Use Launch Shortcut instead of steam.exe anytime you launch Steam
## Revert to Latest

1. Delete `steam.cfg`
    
2. Delete `package\` and `appcache\` contents
    
3. Run: `Steam.exe -forcesteamupdate -forcepackagedownload -exitsteam`
    
4. Launch normally



