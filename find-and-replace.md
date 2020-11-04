# Find and Replace

Prepend a String to the Start of a Document
```bash
# Prepends "# " to first line of testfile 
sed -i '1!b;s/^/\# /g' testfile
```

Combine find and sed Commands with exec
---------------------------------------
### Simple Pattern Replacement in Named Files
Find all files named `.htaccess` and replace the pattern `1.2.3.4` with `5.6.7.8` in place:

```bash
find /var/www/html -type f -name .htaccess -exec sed -i 's/1.2.3.4/5.6.7.8/' {} \;
```
Useful for when an IP address needs to be changed in many `.htaccess` files.

```bash
# Add Markdown h1 tags to all .md files in current directory
find . -type f -name '*.md' -exec sed -i '1!b;s/^/\# /g' {} \;

# Remove any lines beginning with "===" in markdown files in current directory
find . -type f -name '*.md' -exec sed -i '/^===/d' {} \;

# Capture a date pattern in TOML frontmatter of markdown files and clean up:
find . -name '*.md' -o -name '*.markdown' -exec sed -i 's/^date = \([0-9\-]*\).*/date = \1/g' {} \;
```

Remove Spaces
--------------
```bash

#!/bin/bash
compress (){
	sed -i 's/\(\".*\"\)\|\s*/\1/g' "$1"
}

compress "$1"
```

