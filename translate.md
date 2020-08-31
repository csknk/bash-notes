# Translate

The following function slugifies a string:

```
#!/usr/bin/env bash
# slugify.sh

makeslug() {
	tr -dc '[:graph:][:space:]' | tr '[:upper:]' '[:lower:]' | tr ' _' '-' | tr -s '-'
}

echo "$1" | makeslug
```
`tr`: Translate or delete characters. `tr [OPTION] SET1 [SET2]`

* `-d`: delete characters in SET1
* `-c`: use complement of SET1
* `-s`: squeeze repeats of repeated characters in the last specified SET.

Steps:

* `tr -dc '[:graph:][:space:]'`: If a character is a complement of SET1 (i.e. character is NOT graphical or is NOT any kind of space character), delete it.
* `tr '[:upper:]' '[:lower:]'`: Translate uppercase characters to lowercase.
* `tr ' _' '-'`: Translate spaces and underscores to `-`.
* `tr -s '-'`: Squeeze multiple hyphens: `---` becomes `-`. 

Example:
```bash
./slugify.sh "this is a _slug FOR a URL.html"

# Output
this-is-a-slug-for-a-url.html
```

