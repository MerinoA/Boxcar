[Home](home)

## Buttons

Buttons are the building blocks of the Boxcar UI. Buttons are associated to either a [hotbar](hotbars) or a [character](characters).

### Properties

- Title
	+ The title displayed on the button.
	
- Background Color
	+ The background color
	
- Foreground Color
	+ The text color
	
- Timer
	+ A timer in seconds that will start a right to left overlay that will disappear as the timer expires. The timer value is a number of seconds.
	
- Audio Trigger
	+ An audio trigger is a text to speach or wav file name that will play when a timer expires.
	+ You can supply your own .wav files by placing them in the c:/ProgramData/Boxcar directory
		* Do not include .wav extension in the input when setting if you plan to use your own wav files.

	
- Keybind
	+ Keybind is a value that maps the keybind system to the button command execution. See [keybinds](keybinds)
	
- Keybind Priority
	+ If multiple buttons have conflicting keybinds. They keybind priorty will dictate the order in which the commands will be executed in ascending order.
	
- Command
	+ This the heart of the boxcar system. See [commands](commands)