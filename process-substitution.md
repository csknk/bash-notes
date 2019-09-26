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

Reference
---------
* [Process Substitution][1], Bash reference manual

[1]: https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Process-Substitution

