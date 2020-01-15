# BASH Snippets for Generating Keys & Passwords

Create a Keyfile
----------------
Takes 64 bytes from `/dev/urandom`, converts to base 64 (to make the key printable) and removes extra  newlines:

```bash
head -c 64 /dev/urandom | base64 | tr -d '\n' > keyfile.txt
```

As a function:

```bash
#!/bin/bash

function generate_keyfile {
	echo "Enter the number of random bytes you require per key:"
	read nBytes

	echo "Enter the number of random keys required:"
	read nKeys

	for ((i=0; i<$nKeys; i++))
	do
		head -c $nBytes /dev/urandom | base64 | tr -d '\n' >> $1;
		echo >> $1
	done
}
generate_keyfile $1

```
