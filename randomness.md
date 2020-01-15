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

Random Bytes Hexstring
----------------------

Generate a pseudo-random hexadecimal string from `/dev/urandom`:

```bash
xxd -l 8 -p /dev/urandom | tr -d " \n"
```
Function to achieve the same thing - receives a length parameter, which refers to the number of octets to be returned. The default length is 16 bytes. Uses [xxd](http://linuxcommand.org/man_pages/xxd1.html)

```bash

#!/bin/bash
# base64 --wrap=0 /dev/urandom | head -c $LENGTH ; echo ""
# ------------------------------------------------------------------------------
function main {
	if [ -z "$1" ]
	then
		LENGTH=16
	else
		LENGTH=$1
	fi
	echo $(xxd -l "$LENGTH" -p /dev/urandom | tr -d " \n")
}

main $1
```

Random Word Generator
---------------------
```bash
#!/bin/bash

# Random Word Generator
# Resources:
# https://blog.webernetz.net/password-strengthentropy-characters-vs-words/

function set_variables {
	readonly ALL_NON_RANDOM_WORDS=/usr/share/dict/words
	KEYSPACE=$(cat $ALL_NON_RANDOM_WORDS | wc -l)
	NUM=$1
	ENTROPY=$(entropy $KEYSPACE $NUM)
}

# Entropy is defined as log base 2 of Character set to the power of the length.
# In this case, character set is the number of words available to select from and
# the length is the number of pseudorandom words output.
function entropy {
	export WORDSET=$1
	export WORDS=$2
	python3 - <<- EOF
	import math; import os;
	r = math.log(int(os.environ['WORDSET']) ** int(os.environ['WORDS']), 2)
	print(round(r, 2))
	EOF
}

function generate {
	X=0
	WORDS=""
	echo "$1 words pseudo-randomly selected from a keyspace of ${KEYSPACE} words:"

	while [[ "$X" -lt "$1" ]]; do
		random_number=$(od -N3 -An -i /dev/urandom)
		random_number=$(($random_number % ${KEYSPACE}))
		WORD=$(sed ${random_number}"q;d" $ALL_NON_RANDOM_WORDS | tr -dc '[:alnum:]' | tr '[:upper:]' '[:lower:]')
		WORDS="${WORDS} ${WORD}"
		let "X = X + 1"
	done
	echo -e ${WORDS}
	echo "Source of randomness is /dev/urandom."
	echo "Total entropy of this passphrase is: ${ENTROPY}"
}

function main {
	echo "How many words?"
	read N
	if [[ -z $N ]]; then
		N=1
	fi
	set_variables $N
	generate $N
}

main
```
