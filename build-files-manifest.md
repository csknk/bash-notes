Build A Manifest of all Files in Current Directory
==================================================

If you need to build a manifest file that contains each file in the current directory written on a separate line.

```bash
# This includes all directory contents, including subdirectories.
ls -1 > manifest.js

# Same result as above
for f in *; do echo -e $f >> manifest.txt; done

# Fine tune to make a manifest of files only
for f in *; do [[ -f $f ]]  && echo -e $f >> manifest.txt; done

# Fine tune - files with extension .md only
for f in *.md; do [[ -f $f ]]  && echo -e $f >> manifest.txt; done
```
Once you've built a manifest, you may need to convert it to JSON format. Use `jq` for this:

```bash
# Process manifest.txt into a json file. Pipe result back to jq
# to remove the trailing newline.
jq -R -s 'split("\n")' < manifest.txt | jq '.[:-1]' > manifest.json

# Output:
cat manifest.json 
[
  "file1.md",
  "file2.md",
  "file3.md"
]


```

Prepend text to all Files in a Directory
----------------------------------------
To add YAML frontmatter to all files:

```bash
# echo the new lines in front of the cat output of each file:
for f in *.md; do echo -e "---\n---\n$(cat $f)" > $f; done
```

References & Resources
----------------------
* [SO question][1]

[1]: https://stackoverflow.com/questions/26287130/converting-lines-to-json-in-bash
