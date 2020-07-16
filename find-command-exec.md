# Using the find Command With exec

Using `find` with the `-exec` flag causes the command to be executed once for each file found:

```bash
# Find all files at the current level that have the type file
# Pass each file to `sha256sum` and output to stdout:
find . -maxdepth 1 -type f -exec sha256sum {} \;

# As above, but write results to a file:
find . -maxdepth 1 -type f -exec sha256sum {} \; > hashes.txt
```

The general formula is:

```bash
find <path> [Options] -exec <command> {} ;
```
The string "{}" is replaced by the current file name being processed. All following arguments are taken as arguments to `<command>` until a `;` is encountered.

**NOTE: you must escape the semicolon wiht a backslash**.

xargs
-----
Do the same with `xargs`:

```bash
find . -maxdepth 1 -type f | xargs sha256sum
```

Filtering
---------
* `-name`: Takes a glob, e.g. `find . -name "*.o"` finds all `*.o` files
* `-iname`: As above, case insensitive. `find . -name "*.html"` finds  `*.html` and `*.HTML` files
* `-path`: Same as `name`, but with full path - `*` matches `/` and leading dots
* `-or`: Combine filters with a logical OR
* `-and`: Implicit between filters, e.g. `find . -name "index*" -type f` matches all files `index*`

```bash
# Find all markdown files in current directory 
find . -name ".md" -or -name "*.markdown" -type f 
```
