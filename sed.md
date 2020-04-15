# Sed
`sed` is a stream editor for filtering & transforming text.

Get a section from a document:

```bash
# Get lines 20 to 42 from myFile.txt and print them.
sed -n '20,42p' myFile.txt

# Get first 5 lines
sed -n '1,5p' myFile.txt
```
Note that the range is `[first, last]` - inclusive - and the initial element is indexed as 1.
