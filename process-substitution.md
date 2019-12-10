Process Substitution
====================
If you need to pass the output of a command to another command that is expecting a file, process substitution can be useful.

Process substitution allows a process’s input or output to be referred to using a filename. It takes the form of `<(list)` or `>(list)` for input and output respectively.

For example, to perform a sha256 hash on the string "foo", when the `sha256sum` command expects a file:

```bash
sha256sum <(echo -n "foo")
```

Note that spaces are not allowed between `<` and `(`.

> Process substitution is supported on systems that support named pipes (FIFOs) or the `/dev/fd` method of naming open files.
>
> Bash reference manual

Not Needed for sha256sum
------------------------
After reading the man page for `sha256sum` it's clear that if the programme does not receive a filename as an argument, it reads standard input.

This means that we don't need process substitution in this case - the following works:

```bash
echo -n "foo" | sha256sum

# Just the hash:
echo -n "foo" | sha256sum | awk '{print $1}'
```
Note `-n` option for echo - if not included, the stdin passed to `sha256sum` will include a newline.

Reference
---------
* [Process Substitution][1], Bash reference manual

[1]: https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Process-Substitution

