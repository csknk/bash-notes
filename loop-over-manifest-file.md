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

# In general:
for LINE in $(cat FILE); do COMMAND; done
```

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


