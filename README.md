# freewrite Focus Mode Shortcut

A macOS Shortcut that instantly hides all running applications and launches freewrite in fullscreen mode, creating a distraction-free writing environment with a single keyboard command.

## Features

- **One-key activation**: Launch with a customizable keyboard shortcut
- **Instant focus**: Hides all running applications to eliminate distractions
- **Automatic fullscreen**: Opens freewrite in fullscreen mode automatically
- **Native macOS**: Uses the built-in Shortcuts app (macOS 12+ required)

## Installation

### Option 1: Import the Shortcut File (Recommended)

1. Download the `freewrite-Focus-Mode.shortcut` file from this repository
2. Double-click the file to open it in the Shortcuts app
3. Click "Add Shortcut" to import it
4. Follow the [Permission Setup](#permission-setup) instructions below
5. [Assign a keyboard shortcut](#assigning-a-keyboard-shortcut)

### Option 2: Manual Setup

If you prefer to build the shortcut yourself or want to customize it:

1. Open the **Shortcuts** app on your Mac
2. Click the **+** button to create a new shortcut
3. Add the following actions in order:

#### Action 1: Hide All Applications
- Add **"Run AppleScript"**
- Paste this code:
```applescript
tell application "System Events"
    set visible of every process to false
end tell
```

#### Action 2: Brief Wait
- Add **"Wait"**
- Set duration to **0.5 seconds**

#### Action 3: Open freewrite
- Add **"Open App"**
- Select **"freewrite"** from the app list

#### Action 4: Wait for Launch
- Add **"Wait"**
- Set duration to **1 second**

#### Action 5: Enter Fullscreen
- Add **"Run AppleScript"**
- Paste this code:
```applescript
tell application "System Events"
	tell process "freewrite"
		click menu item "Enter Full Screen" of menu "View" of menu bar 1
	end tell
end tell
```

4. **Name your shortcut**: Click the title and rename it to "freewrite Focus Mode"

## Permission Setup

For the shortcut to work properly, you need to grant specific permissions to the Shortcuts app:

### Enable Accessibility Access

1. Open **System Settings** (click Apple menu  → System Settings)
2. Navigate to **Privacy & Security** → **Accessibility**
3. Find **Shortcuts** in the list and toggle it **ON**
4. If Shortcuts isn't listed:
   - Click the **+** button
   - Navigate to **Applications** and select **Shortcuts.app**
   - Toggle it **ON**

### Restart Shortcuts

After granting permissions, quit and reopen the Shortcuts app for changes to take effect.

## Assigning a Keyboard Shortcut

1. In the **Shortcuts** app, select your "freewrite Focus Mode" shortcut
2. Look at the **details panel on the right**
3. Click **"Add Keyboard Shortcut"** (or the keyboard shortcut field)
4. Press your desired key combination, for example:
   - `⌘ Cmd + ⇧ Shift + F`
   - `⌘ Cmd + ⌥ Option + F`
   - `⌃ Control + ⌥ Option + F`
5. The shortcut is saved automatically

**Alternative method**: Right-click the shortcut → select "Add Keyboard Shortcut"

## Usage

Once set up, simply press your assigned keyboard combination from anywhere on your Mac. The shortcut will:

1. Hide all currently running applications
2. Launch freewrite
3. Automatically enter fullscreen mode

## Troubleshooting

### Error: "Shortcuts is not allowed to send keystrokes"

**Solution**: You need to grant Accessibility permissions (see [Permission Setup](#permission-setup))

### freewrite doesn't appear in the app list

- Try typing "freewrite" manually in the Open App action
- Check the exact name in your Applications folder
- The app might be named slightly differently

### Apps don't hide

Make sure you've granted Automation permissions for System Events (see [Permission Setup](#permission-setup))

## Customization

### Change the target application

Replace "freewrite" in Actions 3 and 5 with any other application name (e.g., "Notes", "TextEdit", "Visual Studio Code")

### Adjust timing

If the fullscreen action happens too quickly or slowly, modify the wait durations:
- Increase Action 4 wait time if the app needs more time to launch
- Increase the `delay 0.5` in Action 5 if fullscreen isn't activating

### Change hide behavior

To minimize windows to the dock instead of hiding apps, replace Action 1 with:
```applescript
tell application "System Events"
    tell (every process whose visible is true)
        set collapsed of windows to true
    end tell
end tell
```

## Requirements

- macOS 12 (Monterey) or later
- freewrite app installed
- Shortcuts app (built-in)

## Contributing

Found a better way to implement fullscreen? Have suggestions for improvements? Feel free to open an issue or submit a pull request!

## License

MIT License - feel free to modify and share!

## Credits

Created for writers who want instant access to a distraction-free writing environment.

---

**Note**: This shortcut was designed for freewrite, but can be easily adapted for any application that supports fullscreen mode.
