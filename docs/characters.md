[Home](home)

# Characters
A character is an entity in Boxcar that has 12 associated command [buttons](buttons) and a one character button that can be rendered in Boxcar [windows](windows). 

A character can be associated to a game instance via the Game Clients tab and sync features. 

Boxcar has no knowledge of the inner workings of the game or application you are associating to the character.

## Properties
- Enabled
	+ This property when disabled will hide a character from drop down lists on the sync page and stop the associated command and character button from being rendered in any Boxcar overlay window.
	

- Window
	+ This property is the window that the command buttons and character button will be rendered in. Defaults to main.
	

- Order
	+ This property is the sort order of the characters. 
	+ The character list is the order in which characters will be rendered in final windows, lists, etc.
	+ You can edit the order by drag and dropping the characters in the character list. Defaults to the order of creation.
	
- Keybind
	+ A keybind that will swap to this game client.
	+ Refer to [keybinds](keybinds) for syntax.
	
## Requirements
 - Character names must be unique.
 
## Optional
- Username
	+ Providing a valid user name has benefits in the auto launch feature.
	
- Password
	+ Providing a valid password has benefits in the auto launch feature.

