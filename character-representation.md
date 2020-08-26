# Character Representation

Represent a string as ASCII hexadecimal codes:

```bash
echo dave@example.com | xxd -ps

# Output
64617665406578616d706c652e636f6d0a
```

Reverse the process:

```bash
echo 64617665406578616d706c652e636f6d0a | xxd -ps -r

# Output:
dave@example.com
```

Binary
------

To binary:

```bash
echo david | xxd -b

# Output:
00000000: 01100100 01100001 01110110 01101001 01100100 00001010  david.
```
