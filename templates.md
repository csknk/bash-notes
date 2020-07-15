# Templates
Assuming a template file `template.txt` exists in the curretn directory, where the strings `id` and `name` should be substituted.

m4 Solution 
-----------
m4 is a templating language developed by none other than Kernighan & Ritchie. It's included in all UNIX-like systems.

```bash
#!/bin/bash
template=template.txt
id=42
name="csknk"
# To variable
inserted=$(cat $template | m4 -DID="$id" -DNAME="$name")
# To output file
cat $template | m4 -DID="$id" -DNAME="$name" > outm4.txt
# Same as above:
m4 -DID="$id" -DNAME="$name" < $template > outm4-2.txt
```

sed Solution
------------
```bash
# To variable
sed_test=$(sed -e "s/ID/${id}/g" \
-e "s/NAME/${name}/g" \
< $template)
echo $sed_test

# Write to file, useful for generating config files:
sed -e "s/ID/${id}/g" \
-e "s/NAME/${name}/g" \
< $template > output.txt
```

References
----------
* [m4 Wikipedia][1]
* [Notes on m4][2]

[1]: https://en.wikipedia.org/wiki/M4_(computer_language)
[2]: https://mbreen.com/m4.html
