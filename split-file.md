# Split a File By Pattern Matching

Split markdown file on heading 2 pattern:

```bash
csplit my-original-file.md '/^\#\#\s/' '{*}' --prefix=my-subfile --suffix-format="%d.md"
```
