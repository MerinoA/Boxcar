🏠 [Home](boxcar://home)

# 🎭 Characters  
A **Character** in Boxcar is an entity with **12 associated command** [buttons](boxcar://buttons) and a **character button** that can be rendered in Boxcar [windows](boxcar://windows).  

Characters can be associated with a **game instance** via the **Game Clients** tab and sync features.  

> **Note:** Boxcar has no knowledge of the inner workings of the game or application you are associating to the character.

---

## ⚙️ Properties  

- **Enabled**  
  - When disabled, windows will not render the character or its 12 buttons, nor will any associated keybinds be active.

- **Window**  
  - Determines which window the **command buttons and character button** will be rendered in.  
  - **Default:** `main`.

- **Order**  
  - Sets the **sort order** of characters.  
  - The character list determines how characters will be displayed in final **windows, lists, etc.**  
  - You can **drag and drop** characters in the list to rearrange them.  
  - **Default:** Order of creation.

- **Keybind**  
  - A **keybinding** that will invoke the **character button** 
  - See [keybind syntax](boxcar://keybind) for details.

- **Categories**  
  - A **string identifier** used to target groups of characters with the `'all'` command type. Supports comma separated list to associate a character with multiple categories. `dps,ranged` as an example.
  - See [commands](boxcar://commands) for more details.

---

## ✅ Requirements  
- **Character names must be unique.**  

---

## 🎯 Optional  

- **Username**  
  - Providing a valid username enables **auto-launch** features.  

- **Password**  
  - Providing a valid password also benefits **auto-launch** features. 

Username and passwords are stored **encrypted** in the ini file.