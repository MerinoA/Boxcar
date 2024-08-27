[Home](home)

## LAN


LAN support:


Windows settings must be correct and computers need to be discover-able.
Boxcar needs to be given firewall access to private network.

The LAN uses UDP broadcasting over a specified port to communicate between local computers. Computers with the specified LAN name will act on messages received for that LAN name.


Command:
send:LAN_NAME:COMMAND
         
Prefix your command with "send" then use ":" as the separator. 
The COMMAND is just the normal command syntax and LAN_NAME is the name set on the LAN instance of boxcar you are targeting.


Targeting Multiple instances. This is done by appending addtional LAN_NAME:COMMAND using the : separator

**send:instance1:bob|key.1:instance2:sam|key.3**

### Special Instance names

- ALL
	+ Targets all boxcar instances connected. Including the sender.
	
- ALLX
	+ Targets all boxcar instance connected excluding the sender.