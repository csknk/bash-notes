# BASH Test

Negation
--------
The `test` command has a "not" logical operator: `!`.

`! EXPRESSION` returns true if `EXPRESSION` is false.

For example:

```bash
[[ ! -f ${input} ]] && { echo "$input is NOT a file"; } || { echo "$input IS a file."; }

```

* `( EXPRESSION )` - EXPRESSION is true
* `! EXPRESSION` - EXPRESSION is false
* `EXPRESSION1 -a EXPRESSION2` - both EXPRESSION1 and EXPRESSION2 are true
* `EXPRESSION1 -o EXPRESSION2` - either EXPRESSION1 or EXPRESSION2 is true
* `-n STRING` - the length of STRING is nonzero
* `STRING` - equivalent to -n STRING
* `-z STRING` - the length of STRING is zero
* `STRING1 = STRING2` - the strings are equal
* `STRING1 != STRING2` - the strings are not equal
* `INTEGER1 -eq INTEGER2` - INTEGER1 is equal to INTEGER2
* `INTEGER1 -ge INTEGER2` - INTEGER1 is greater than or equal to INTEGER2
* `INTEGER1 -gt INTEGER2` - INTEGER1 is greater than INTEGER2
* `INTEGER1 -le INTEGER2` - INTEGER1 is less than or equal to INTEGER2
* `INTEGER1 -lt INTEGER2` - INTEGER1 is less than INTEGER2
* `INTEGER1 -ne INTEGER2` - INTEGER1 is not equal to INTEGER2

File Testing
------------

* `-b filename` - Block special file
* `-c filename` - Special character file
* `-d directoryname` - Check for directory Existence
* `-e filename` - Check for file existence, regardless of type (node, directory, socket, etc.)
* `-f filename` - Check for regular file existence not a directory
* `-G filename` - Check if file exists and is owned by effective group ID
* `-G filename set-group-id` - True if file exists and is set-group-id
* `-k filename` - Sticky bit
* `-L filename` - Symbolic link
* `-O filename` - True if file exists and is owned by the effective user id
* `-r filename` - Check if file is a readable
* `-S filename` - Check if file is socket
* `-s filename` - Check if file is nonzero size
* `-u filename` - Check if file set-user-id bit is set
* `-w filename` - Check if file is writable
* `-x filename` - Check if file is executable
* `file1 -ef file2` - Check if file1 and file2 have same device and inode numbers
* `file1 -nt file2` - Check if file1 is newer than file2 (modification date)
* `file1 -ot file2` - Check if file1 is older than file2

Use with the `test` command or the `[[ ]]`

References
----------
* [test man page][1]

[1]: http://man7.org/linux/man-pages/man1/test.1.html
