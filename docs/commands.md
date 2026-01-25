🏠 [Home](boxcar://home)

# ⚡ Commands

A **command** in Boxcar is a set of instructions that Boxcar will execute in order. Each instruction is referred to as an **Action**.  
The **command syntax** uses the **pipe symbol** `|` to separate actions.

> **Note:** Commands are **not case sensitive**.

---

## 🛠️ Actions

An **Action** can have several components. The first component is always the **action type** (except for one special case where the action type can be omitted). All other components are separated by a `.` period character and are considered the **inputs** for that action.

### 📝 Action Types

- **Character**  
  - This action type swaps to a specific **game instance** associated with the character name provided as the first input.  
  - **Syntax:** `character.<name>`  
  - **Note:** This is the only action type where the action type can be omitted. Boxcar will automatically try to resolve an unknown action type as a character. You can simply type the **name of your character** to swap to that instance.  
  - **Example:** 
    ```
    character.MyCharacter
    /**
    or omit the character action type prefix.

    Character action and All action are the only action that support omitting the action prefix.
    **/
    MyCharacter
    ```  
  - **Special:** `"active"` swaps to the character that was active when the command was issued.  
  - **Default:** If the last action in a command is not a **character action**, Boxcar will append a `character.active` action to return you to your last active instance.

- **Delay**  
  - Introduces a **delay** during command execution. Actions are executed sequentially, with each action completing before the next starts.  
  - **Syntax:** `delay.<milliseconds>`  
  - **Example:**
    ```
    delay.1000 // introduces a 1-second delay.
    ```

- **Key**  
  - Sends a **keyboard input**.  
  - **Syntax:** `key.<keypress>`  
  - The first input is the key to press.  
  - **Example:**
    ```
    key.1 // will press the 1 key.  
    ```  
  - You can append an `x<n>` modifier to press the key multiple times.  
  - **Example:** 
    ```
    key.1x3 // will press the 1 key 3 times.
    ```  
  - The second input is the **hold duration** (optional), in milliseconds.  
  - **Example:**
    ```
    key.1.100 // will press the 1 key and hold it for 100ms.
    ``` 

- **Mod**  
  - Applies **key modifications** to the input key press.  
  - The first input is the modifier (Shift, Alt, Ctrl) separated by `+`.  
  - The second input is the key to press, following the same rules as the **Key** action.  
  - The third input is the **hold duration** (optional).  
  - **Valid Mods:** `Shift`, `Alt`, `Ctrl`  
  - **Example:** 
    ```
    mod.shift.key.1.100 // will hold the Shift key and press the 1 key for 100ms.
  
    OR
    
    mod.shift.1.100 // will hold the Shift key and press the 1 key for 100ms.
    ``` 

- **LMouse**  
  - The first input is the **x-y coordinates** for the mouse click.  
  - **Example:**
    ```
    600-700 // for x=600 and y=700
    ``` 
  - The second input is an **optional delay** before and after the click, in milliseconds (defaults to 200ms).  
  - **Example:** 
    ```
    LMouse.600-700.200 // will click at coordinates 600-700 with a delay of 200ms
    ``` 

- **RMouse**  
  - Same as **LMouse**, but for a **right-click**.

- **MouseMove**  
  - The first input is the **x-y coordinates** for mouse movement.  
  - You can also use `"restore"` to move the mouse to the last stored position.  
  - **Example:** 
    ```
    mousemove.600-700 // moves the mouse to coordinates 600-700.
    ``` 
  - **Example:** 
    ```
    mousemove.restore // restores the mouse position from the previous move.
    ``` 
  - **Note:** Always use `restore` before another `mousemove`.

- **MouseClick**  
  - The first input is either **left** or **right** for the corresponding mouse button.  
  - The second input is an **optional hold duration** for holding down the click before releasing.  
  - **Example:**
    ```
    mouseclick.left.100 // will click and hold the left mouse button for 100ms.
    ``` 

- **Type**  
  - Types any text following `type.`  
  - **Syntax:** `type.<text>`  
  - **Example:** 
    ```
    type.Hello World! // types the text "Hello World!".
    ``` 

- **All**  
  - The only input is an **optional character category type**.  
  - **Example:** 
    ```
    all // target@ 
  
    all.dps // target all characters in dps category

    all.healer // target all characters in the healer category  
    ``` 
  - Categories can be set in the **Character tab**.

---

## 🕒 Milliseconds

Any action that accepts **milliseconds** (such as delay or key hold) can use the **range format** `<lowerBound>-<upperBound>` to define a **random number** of milliseconds.
```
// Example:
// A delay from 1 to 3.5 seconds

delay.1000-3500

// A key press held for 0.5 to 1.0 seconds
key.1.500-1000
```

---

## 🤯 Complex Command Example

```

/**

    This is an example of an advanced command to send commands to multiple characters
    running on the same computer.

    The command will change to character 1 and press 1, wait 2 - 4 seconds then
    change to character 2 press shift alt and 2 then 
    change to character 3 and left click the mouse at 659 - 745 200ms after moving the mouse to those cords then
    change to character 4 and press the left key and hold it for 100 ms
**/

character1|key.1|delay.2000-4000|character2|mod.shift+alt.key.2|character3|lmouse.659-745.200|character.4|key.left.100

/**
    If these characters were all on seperate pcs the command would need to be
    modified to send the command portions to specific pc identifiers
**/

send:pc1:character1|key.1:pc2:character2|mod.shift+alt.key.2:pc3:character3|lmouse.659-745.200:pc4:character4|key.left.100

```

---

## 🚫 Deprecated Actions

These actions are still functional but are no longer being supported. It's recommended to use **Key** and **Mod** going forward.  

- `hkey` → press and hold  
- `altkey` → alt modifier  
- `ctrlkey` → ctrl modifier  
- `shiftkey` → shift modifier  
- `hctrlkey` → ctrl modifier + press and hold  
- `haltkey` → alt modifier + press and hold  
- `hshiftkey` → shift modifier + press and holdD