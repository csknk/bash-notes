# Check a Programme Exists on the System

Demo programme:

```bash
#!/bin/bash

prog_exists() {
	# redirect stdout - it's not needed in this context
	type "$1" > /dev/null 2>&1

	# Return 0 if programme exists, otherwise an integer
	return $?
}

[[ -z $1 ]] && exit 

# Exit status of 0 evaluates to true - anything else, false. 
if prog_exists "$1"; then
	echo $?
	echo "yes, $1 exists."
else
	echo $?
	echo "no, $1 does not exist."
fi


```
