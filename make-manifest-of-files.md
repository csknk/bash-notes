# Make a Manifest of Files in Current Dir

```bash
#!/bin/bash

for f in *.md;
do
	# Exclude certain files - in this case, README.md
	[[ "$f" == "README.md" ]] && continue;
	# Write all files into manifest.txt
	[[ -f $f ]] && echo -e $f >> manifest.txt;
done

# jq used in this case to make a json manifest - jq is non-standard on Bash
jq -R -s 'split("\n")' < manifest.txt | jq '.[:-1]' > .vuepress/manifest.json
```
