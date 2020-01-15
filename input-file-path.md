# Input File Path

```bash

function select_keyfile {
	echo "Enter a path to a keyfile"
	# Loop until user inputs a valid file path
	while read KEYFILE && [[ -z "$KEYFILE" ]] || [[ ! -f "$KEYFILE" ]]; do
		[[ $KEYFILE == -1 ]] && break
		echo "Please enter a valid file path."
	done
}

```
