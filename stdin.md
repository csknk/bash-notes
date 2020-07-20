# Getting data via stdin

Select
------
Generates a menu from a list of items, construction is like a for-loop:

```
select ITEM in [LIST]
do
	[COMMANDS]
done
```
`[LIST]` may be:
* A collection of strings separated by spaces
* A range of numbers
* The output of a command
* An array

You can define a custom prompt for the construct with the `PS3` environment variable.

When invoked, each item from the list/collection is printed to stderr, preceded by a number (key).

If the user enters a valid key, the value of `ITEM` is set to the corresponding value associated with the selected key.

If the user input is empty, the prompt and list are displayed again.

You probably need a `case` statement to do something useful with the selection, and to control the break:

```bash
#!/bin/bash

PS3="Please enter a choice: "
options=("/tmp will be lost on reboot" "Select a data directory")
select X in "${options[@]}" exit
do
	case $X in
		exit)
			echo "Exiting..."
			break;;
		*)
			echo "You selected $X"
			echo "Key value was: ${REPLY}"
			break;;
	esac
done
```
