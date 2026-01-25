🏠 [Home](boxcar://home)

# 🚀 Auto Launch

Auto Launch will launch a game client for each enabled character.

The game client is launched by a defined path to an executable file.
This is supported by any game that can have its executable file directly invoked.

The system will wait for the process’s main window to be created. 

In addition to defining the executable to launch you can also define args to be passed when that executable is launched. For example the everquest game takes the patchme argument.

---

## 📄 Path to Executable

The executable is the game's exe file that you want to launch. We will use **EverQuest** as an example.

- In the EverQuest directory, you will find the `eqgame.exe` file.  
  You can get the path to the executable by right-clicking the file and selecting **Copy as Path**.

- Paste this path into the **Path to Executable** field.  
  **Do not** include any quote marks.

---

## 🔧 Executable Args

Some executables support passing command line arguments when being invoked. This field supports providing that text.

There are 2 special strings that can be used in the arguments field: `[username]` and `[password]`.  
These strings will be replaced with the username and password stored for the character being launched.

---

## ⚡ Auto Launch Command

Once a process is launched and the window is created, the **Launch Command** will be executed. The launch command uses the same syntax as the game [commands](boxcar://commands).

There are 2 custom Actions that can be used in the launch command that are only valid in auto launch:

- **password**  
  This will type the password associated with that character.

- **username**  
  This will type the username associated with that character.

Example:
```js
/**
The below command will wait 5 seconds after launch, then type the password
then hit the enter key, then wait 5 seconds then hit the enter key again.
**/

delay.5000|password|key.enter|delay.5000|key.enter
```

## Character specific auto launch.

In the character edit screen you can define character specific auto launch settings. This is useful if the game you are playing require different install locations etc. Or for a specific character you want to do a extra delay in a command. etc.

