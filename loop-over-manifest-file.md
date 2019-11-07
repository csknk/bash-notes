Loop Over Lines in a Manifest File
==================================
If you have stored data as lines in a text file, it's easy to loop over the data with BASH.

Method 1: Use Cat
-----------------
Use a subshell `$(command)` to output the list in a standard Bash for loop:

```bash
#!/bin/bash
# the `manifest` file contains a number of lines
for line in $(cat manifest); do
	echo "Downloading ${line}..."
	wget "${line}"
done
```
In general:

```bash
for LINE in $(cat FILE); do COMMAND; done
```

This is a more complete version that loops over a manifest file that is supplied as a command line argument, using each line as a command line argument for a command:

```bash
#!/bin/bash
[[ $# -eq 0 ]] && { echo "Please supply a target file: $(basename $0) <path/to/file>"; exit 1; }

for line in $(cat ${1}); do
	echo "testing using input: ${line}"
	./bin/main ${line}
done
```
Just add all test input files as separate lines in a manifest file, and pass the manifest to the script.

Method 2: Input Redirection
---------------------------
Redirect a file into a while loop as a one-liner:
```bash
while read l; do echo "${l}"; done < file-1.txt

# In general:
while read LINE; do COMMAND; done < FILE

# or
while read LINE; do
	COMMAND;
done < FILE

# Example - read all users from `/etc/passwd` file:
while read line; do echo "$line" | cut -f1 -d":"; done < /etc/passwd
```


