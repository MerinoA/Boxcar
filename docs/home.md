
# Boxcar Wiki 

**Boxcar** helps coordinate switching between multiple running instances of a game (or other application) while issuing designated keystrokes, mouse actions, and command sequences to those instances.

## 📌 Quick Links

- 🎭 [Characters](boxcar://characters)  
- 🎛️ [Hotbars](boxcar://hotbars)  
- 🔘 [Buttons](boxcar://buttons)  
- 🎒 [Loadouts](boxcar://loadouts)  
- ⚡ [Commands](boxcar://commands)  
- ⌨️ [Keybinds](boxcar://keybind)  
- 🎹 [Supported Keys](boxcar://keypress)  
- 🚀 [Auto Launch](boxcar://launch)  
- 🖥️ [Windows](boxcar://windows)  
- 🌐 [Local Server](boxcar://lan)  
- 🌎 [Global UI](boxcar://ui_settings)  

--- 

## Read this first!

Commands vs Keybinds — what to enter and where
- Commands — the sequences Boxcar will execute when a button runs. Commands are the payload: key presses, mouse actions, delays, character switches and other actions. Commands are normally stored on buttons (for example: `MyChar|key.1|delay.500|mod.ctrl+shift.key.2`).
- Keybinds — the physical keyboard combination you press to trigger a command or to switch characters. Keybinds are mapped to one or more button commands or to a character switch.

Use `key.` and `mod.` when appropriate
- Prefer explicit prefixes to avoid ambiguity:
  - `key.` is the canonical way to indicate a key action (examples: `key.1`, `key.enter`, `key.-`).
  - `mod.` groups modifiers with an action and is useful for complex combinations (example: `mod.ctrl+shift.key.2`).
- Example command (button payload): `MyChar|mod.ctrl+alt.key.F|delay.1000|key.enter`

Quick rules and helpful notes
- Commands are pipe-separated: `Action1|Action2|Action3`.
- Common actions include `key.<key>`, `mod.<modifiers>.<action>`, `delay.<ms>` (or `delay.<min>-<max>` for a random range), `type.<text>`, and `character.<Name>`.
- Use `delay.` between steps to account for client load times and UI transitions.
- Default button wiring: when a character button has no custom command, a sensible default like `CharacterName|key.<n>` is generated. Key mapping for the default row:
  - Buttons 1..9 → `1`..`9`
  - Button 10 → `0`
  - Button 11 → `-`
  - Button 12 → `=`
- Auto‑launch placeholders: use `[username]` and `[password]` inside `ExecutableArgs` or `AutoLaunchCommand` to inject stored credentials during automated launch sequences. Credentials are stored encrypted.

Execution behavior (what happens when a keybind triggers)
- Boxcar will, when possible, bring the assigned game process to the foreground before sending input.
- The keybind listener is temporarily paused while Boxcar executes the mapped commands to avoid reentrant triggers.
- Commands execute sequentially with the configured `Base Delay` between steps.

Quick troubleshooting for keybinds & commands
- Keybinds may not be able to bring a window to the foreground due to Windows OS limitations. You may need to use the autolaunch command. See [here](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-setforegroundwindow#remarks) for details.
- Keybind doesn't fire? Ensure the mapped button or character is `Enabled` and that the button is part of the active set (window/hotbar visibility). Also verify the keybind entry on the Keybinds page.
- Command partially fails or actions are skipped? Add `delay.` steps to handle slow clients. Some games or anti‑cheat tools may block simulated input; try in‑game bindings if simulation fails.
- Buttons run against the wrong target? Check the `Character` name used in the command and confirm the process is correctly assigned on the Game Clients screen.

Where to go next
- Configure characters, buttons and keybinds from the Characters / Buttons / Keybinds pages.
- Tune timing with `Base Delay` and launch timing values in Core Settings.
- Use the manual process search on the Game Clients screen if automatic discovery fails.

---

## ⛓ Syncing Game Clients

The Game Clients screen is where you associate a running process with a `Character`. Boxcar will attempt to discover game processes automatically based on the configured **Game Process Name**.

Tips
- If your game is already running when Boxcar starts it will usually appear automatically.
- If you start the game after Boxcar, use the refresh button to re-scan processes.
- If automatic discovery fails, use the search icon to open the manual process list and select the correct process.
- Once a process is assigned, Boxcar will target that process for bringing to foreground and for simulated input.

Note
- The default game process name is commonly `eqgame` for EverQuest setups; change it in Core Settings if your game uses a different executable name.

--- 

## ⚙️ Core Settings

Core settings control global app behavior and timing. Most values are persisted to the app store and applied immediately.

- **Base Delay (Inherent Delay)** ⏳  
  Global delay (ms) inserted between actions executed by the engine. Default: **150 ms**. Use this to tune reliability for slow clients or high-latency input.

- **Suppress Invalid Commands & Warnings** 🚫  
  When enabled, Boxcar will not show popups for invalid or unmapped commands. Useful when maintaining legacy buttons that reference removed characters or resources.

- **Disable Keybinds Paused Window** ❌🖥️  
  When keybind processing is paused the small "paused" status window can be hidden with this option.

- **Show Hotbar Names** 🔖  
  Toggle whether hotbar (extra row) names are shown in the overlay.

- **Volume Adjuster** 🔊  
  Controls audio trigger volume (0.0–1.0). Use to mute or reduce sound effects from audio triggers.

- **Game Process Name** 🎮  
  The executable/process name Boxcar looks for to auto-detect game clients. Change this if your game uses a different process name.

Other useful tools in Core Settings
- **Restore Keybinds Window** — reset the paused-keybind status window back to top-left if it goes offscreen.
- **Restore Server Window (LAN Status)** — reset the LAN status window position.
- **Open Program Data Folder** — opens the application's data folder in Explorer (contains the `ini` store and logs).
- **Create Desktop Shortcut** — creates a `Boxcar.lnk` shortcut on the current user's desktop.

--- 

## 🧭 Loadouts, Windows & Hotbars

- Loadouts store a named collection of enabled windows, characters, hotbars, plus executable/launch settings. Use loadouts to switch whole setups quickly.
- Windows are overlay containers (the `main` window exists by default). Per-window settings include orientation (`IsVertical`) and `scaleFactor`.
- Hotbars (extra rows) are reusable button rows that can be assigned to windows or tied to a specific character page.

--- 

## 🔐 Auto‑Launch & Credentials

- Boxcar can store per-character or global `Executable` and `ExecutableArgs`, plus an `AutoLaunchCommand` sequence that runs after the game process is detected.
- Placeholders like `[username]` and `[password]` are supported in arguments and launch commands; credentials are stored encrypted.
- Use `delay.` actions in launch commands to accommodate client load and login timing.

--- 

## ⚠ Migration & Compatibility Notes

- On first run after some upgrades Boxcar may migrate timer values (older versions stored timers in seconds). The app runs a migration step during initial load; you may see a brief re-load as timers are updated.
- Some games or anti‑cheat systems may block synthesized input. If key simulation fails, try in-game bindings or alternative timing adjustments.

--- 

## 🛠 Troubleshooting & Tips

- Overlays not visible: ensure the window and its assigned characters/hotbars are enabled, and check the per-window `IsVertical` / scale settings.
- Offscreen status windows: use the Core Settings restore buttons.
- If audio triggers are too loud or silent, check the Volume in Core Settings and the system sound mixer.
- To create a persistent desktop shortcut use Core Settings → Create Desktop Shortcut.
- If processes aren’t discovered, confirm the Game Process Name and use the manual process search.

--- 

If you'd like, the other wiki pages can be revised to match this tone and include concise usage examples, troubleshooting steps, and short command snippets for common workflows.