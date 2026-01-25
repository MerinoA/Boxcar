🏠 [Home](boxcar://home)

# 🌐 Local Server

The local server features within Boxcar allow communication over your local network between PCs running Boxcar.
This can be useful if you desire to play multiple characters across several PCs.

---

## 🆔 PC Identifiers

The PC Identifier is a crucial setting when communicating between instances of Boxcar. This is a human readable and self defined identifier that is used within boxcar [commands](boxcar://commands) to target specific instances of boxcar.
This should be set to some unique value for each computer running Boxcar.

## ⭐🆔 Special PC Identifiers

- **ALL**  
  Targets all Boxcar instances connected, including the sender.

- **ALLX**  
  Targets all Boxcar instances connected, excluding the sender.

---

## 🖥️ Connection Status Window

This is an overlay window that will provide quick access to connectivity actions and displays the current status of the connection.

---

## ✅ Is Server
When this option is checked the instance of boxcar will act as the server for all other instances on the local network. You must have one instance of boxcar set as the server.


## ⚡ Command Syntax:
When wanting to send commands via broadcasting from one PC to another the boxcar button command syntax needs to be edited.

The main change is the addition of a new delineator **:** (colon) and a new prefix (send) to indicate to the command processor that this text can skip all normal processing and be routed to the broadcaster.

1. Start all broadcasting commands with the word **send** followed by a **:** colon.

2. Now that your command looks like **send:** you can begin the pattern  of **ID:COMMAND**
These Can be chainged.

**ID** being the pc identifier for the targeted PC or one of the special PC identifiers

**COMMAND** being a standard boxcar command that will be valid for that instance of boxcar. (character names/categories etc.)

```js
/**
1) prefix command with send
2) target a id
3) provide a command
4) repeat 2 and 3 as necessary
**/

send:pc1:char1|key.1:pc2:char2|key.f:pc3:char3|mod.shift.1

```


### 👪 Targeting Multiple Instances
When wanting to target multiple instances you can use the special PC identifiers to target all or all except the sender. In the scenario where you want to target a subset of those you will need to explicity write the command or have 2 pc's share an identifier.

Sharing an identifier can add complexity.

As shown in the example above the key concept for targeting multiple instances is repeating step 4.

```js
/**
This is an example of explicit targeting.
**/

send:pc1:char1|key.1:pc2:char2|key.f

/**
This is an example of targeting all PCs and all characters.
**/

send:all:all|key.1

/**
This is an example of targeting all pc's except the sending pc and the dps character category.
**/

send:allx:all.dps|key.1

```
## ⚠️ Warning 

PC Identifiers must be unique!

A PC will only execute the first command that it is eligible for. You cannot chain calls in the send commands.


---