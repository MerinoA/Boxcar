🏠 [Home](boxcar://home)

# 🔘 Buttons

Buttons are the building blocks of the Boxcar UI. They are associated with either a [hotbar](boxcar://hotbars) or a [character](boxcar://characters).

---

## ⚙️ Properties

- **Title**  
  - The title displayed on the button.

- **Background Color**  
  - The background color of the button.

- **Foreground Color**  
  - The text color of the button.

- **Timer**  
  - A timer in seconds that triggers a right-to-left overlay that disappears as the timer expires. The timer value is measured in seconds.

- **Audio Trigger**  
  - An audio trigger is a text-to-speech or WAV file name that will play when the timer expires.  
  - You can supply your own .wav files by placing them in the `c:/ProgramData/Boxcar` directory.  
  - *Do not include the `.wav` extension in the input when setting up your own files.*

- **Keybind**  
  - A keybind that maps the keybind system to the button command execution. Refer to [keybinds](boxcar://keybind).

- **Keybind Priority**  
  - If multiple buttons share conflicting keybinds, the keybind priority will determine the order in which the commands are executed. Lower priority values are executed first.

- **Command**  
  - This is the core of the Boxcar system. Refer to [commands](boxcar://commands).

---

## 🔀 Reordering Buttons

Right-click a button and select **Edit Bar** or navigate to edit character or edit hotbar screens via the main settings menu and pencol icons.

Use the left and right arrows to modify the order of the buttons associated to the bar.