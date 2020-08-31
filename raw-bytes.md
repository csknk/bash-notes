# Raw Bytes

Set Raw Bytes
-------------

Make a variable with raw bytes:

```bash
foo=$(printf "%b" '\x64\x0a\x64\x09\x64')

# Or use echo with -e to allow interpretation of backslash escapes:
foo=$(echo -n -e '\x64\x0a\x64\x09\x64')
```

Inspect Raw Bytes
-----------------
```bash
echo -n "$foo" | xxd

# Output:
00000000: 640a 6409 64                           d.d.d
```

Note that if you don't wrap the variable in double quotation marks, echo won't expand special values and `xxd` may receive something unexpected. For example:

```bash
echo -n $foo | xxd                                                                                    │

# Output - note that special characters are replaced by space characters:
00000000: 6420 6420 64                             d d d
```

