
# Boxcar  

**Boxcar** is an application that helps coordinate **switching between multiple instances** of an application while simultaneously **issuing designated keystrokes**.  

---

## 📌 Quick Links

- 🎭 [Characters](boxcar://characters)
- 🎛️ [Hotbars](boxcar://hotbars)
- 🔘 [Buttons](boxcar://buttons)
- ⚡ [Commands](boxcar://commands)
- ⌨️ [Keybinds](boxcar://keybind)
- 🎹 [Supported Keys](boxcar://keypress)
- 🚀 [Auto Launch](boxcar://launch)  
- 🖥️ [Windows](boxcar://windows)
- 🌐 [Local Server](boxcar://lan)
- 🌎 [Global UI](boxcar://ui_settings)  

---

## ⛓ Syncing Game Clients

The first screen of boxcar is the Game Clients screen, this screen is where you associate a running process to a character. 

Boxcar will automatically attempt to sync a list of processes based on the Game Process name from the core settings at launch.

If you launch the game after boxcar is running you can use the refresh icon button to attempt to automatically discover and list the game.
If the game you are attempting to sync with does not appear, use the search icon to bring up the manual process search window.

The manual process search window will list all the processes running on your machine.

---

## ⚙️ Core Settings 

Boxcar provides several core settings that allow users to customize how the application behaves.  

- **Base Delay** ⏳  
  Defines the inherent delay (in milliseconds) for any action within the system. The default is **150ms**.  

- **Suppress Invalid Commands & Warnings** 🚫  
  Disables the warning pop ups for invalid commands such as unmapped characters etc. Useful if you drop characters from your loadouts, but want to maintain your buttons commands.  

- **Disable Keybinds Paused Window** ❌🖥️  
  Prevents the keybinds paused window from being displayed when keybinds are paused.  

- **Volume Adjuster** 🔊  
  Controls the volume of sounds produced by Audio triggers.  

- **Game Process Name** 🎮  
  Specifies the process name of the game that Boxcar should detect for **Auto Sync** functionality.  