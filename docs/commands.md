## Commands

A command in Boxcar is essentially a set of instructions that Boxcar will execute in order. Each instruction we will refer to as an Action.

The command syntax uses the pipe symbol to separate these actions. 

Use "|" to separate actions within a single command.

Commands are not case sensitive.


### Actions

An Action can have several components. The first component is always the action type (except for 1 special case where the action type can be omitted. More on this later.) All other components of an Action are separated by a "." period character. The other components of an Action are considered its inputs. 

#### Action Types

- Character
	+ This action type is swapping to a specific game instance associated to the character name given as the first input.
	+ **character.\<name>**
	+ Character action type is the ONLY action type where the action type can be omitted. Boxcar will try to resolve any unknown action type as a character. This means you can simply type 
	**\<nameOfYourCharacter>** to swap to that instance.
	+ "active" is a special character input that will swap to the character that was active when the command was issued.
	+ If the last Action in a command is not a character command, Boxcar will default append a character.active Action to the end of a command. That way simple commands will always return you to your driving instance.
- Delay
	+ Delay allows you to introduce some delay at any point in the execution of the command. Actions are executed in order and to their completion.
	+ The input of delay is milliseconds. **delay.\<milliseconds>**.
- Key
	+ The most basic keyboard input command.
	+ The first input is a **keypress**
		* See [Supported keys](keypress) for all the valid input formats.
		* Any *keypress* can have a **x\<integer>** appended to it to make Boxcar spam that key n number of times. Example **key.1x3** will press the 1 key 3 times.
	+ The second input is a hold duration and IS optional.
		* This is a amount of milliseconds to hold the key down.
		* Example: **key.1.100** this will press the 1 key and hold it for 100 milliseconds. You can combine this with the x modifier. Example: **key.1x4.100** this will press and hold the 1 key four times for 100 milliseconds each time.
- Mod
	+ The first input of the Mod action is the types of key modifications separated by "+" the plus sign.
	+ The Second input of the mod action is the **keypress**. This key press follows all the rules mentioned in the Key action section.
	+ The third input is the hold duration that follows the same rules mentioned in the Key action section.
		* Valid Mods
			- Shift
			- Alt
			- Ctrl
			

### Milliseconds
Any action that accepts milliseconds as an argument for delay or key hold can use the format \<lowerBound>-\<upperBound> to define a random number of milliseconds. Using the dash"-" symbol.
```
// Example:
// A delay from 1 to 3.5 seconds

delay.1000-3500

// A key press held for 0.5 to 1.0 seconds
key.1.500-1000
```
			

### Deprecated Actions
These are actions that still work but are no longer being supported.
If you are using these they will continue to work but you can update to using just Key and Mod going forward. 

- hkey -> press and hold
- altkey -> alt modifier
- ctrlkey -> ctrl modifier
- shiftkey -> shift modifier
- hctrlkey -> ctrl modifier plus press and hold
- haltkey -> alt modifier plus press and hold
- hshiftkey -> shift modifier plus press and hold
			
