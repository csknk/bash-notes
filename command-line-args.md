Command Line Arguments in Bash
==============================
Add a one-line guard statement in Bash:

```bash
[[ $# -eq 0 ]] && { echo "Please supply a target file: $(basename $0) <path/to/file>"; exit 1; }
```

Note that multiple commands in the curly braces must each be terminated with a semi-colon.

Note that there must be:

* A single space character between each curly brace and the contents.
* A single space between the [[ and ]] characters.

The Bash special variable $# refers to the number of command line arguments. $(basename $0) refers to the current script name.
