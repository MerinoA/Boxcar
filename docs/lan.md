🏠 [Home](boxcar://home)

# 🌐 Local Server

The local server features within Boxcar allow communication over your local network between PCs running Boxcar.
This can be useful if you desire to play multiple characters across several PCs.

---

## 🆔 PC Identifiers

The PC Identifier is a crucial setting when communicating between instances of Boxcar. This is a human readable and self defined identifier that is used within boxcar [commands](boxcar://commands) to target specific instances of boxcar.
This should be set to some unique value for each computer running Boxcar.

---

## 🖥️ Connection Status Window

This is an overlay window that will provide quick access to connectivity actions when disconnected and displays the current status of the connection.

---

## ✅ Local Server VIA TCP

The prefferred method of connecting your computers to one another is via TCP socket connections.

In this method you will have your main PC start a server with a defined port number. Once the server is started the server's IP and port will be displayed in the settings pane.

This IP can change session to session if your network is using dynamic IPs, assigning your main PC a dedicated IP can make connecting session to session more seamless.

### Connecting

Once the server is started by the main PC you will need to enter the IP and port via the settigns -> local server page. These will be persisted in the ini file between sessions. 

With the provided details you can click the connect button.

### Debugging

Boxcar provides a console on the settings page for local server that displays:

- Connection success / failure
- Server start / stop
- Server heartbeat
- Broadcasting messages
- Messages received
- Commands executed

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
In this example we will incorporate the use of ALLX (all but sender) and the use of
the character category dps to make all dps characters do mod.shift.1
**/

send:pc1:char1|key.1:pc2:char2|key.f:ALLX:all.dps|mod.shift.1

```

## ⭐🆔 Special PC Identifiers

- **ALL**  
  Targets all Boxcar instances connected, including the sender.

- **ALLX**  
  Targets all Boxcar instances connected, excluding the sender.

---

## 🚫 Deprecated LAN Support VIA UDP

This method is simpler but may not work if the network setup is incorrect.

- **Windows Settings:**  
  The necessary settings must be correct, and the computers must be discoverable.  
  Boxcar needs to be given firewall access to the private network.

- **LAN Communication:**  
  The LAN uses UDP broadcasting over a specified port to communicate between local computers.  
  Computers with the specified LAN name will act on messages received for that **PC identifier**.

### ⚠️ Warning 

This method is deprecated. Do not post questions about this method in discord without trying the TCP based solution above.