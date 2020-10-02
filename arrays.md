#  BASH Arrays

Define an array by enclosing elements in parenthesis:

```bash
arr=(1 2 3)
```

If you have space separated values, this is an easy way to convert them to an array.

```bash
var="foo bar baz"
my_array=($var)

for el in ${my_array[@]}; do echo ${el}; done
# Output
foo
bar
baz
```
Add to an Array in a Loop
-------------------------
### Method 1
Loop through an array of values, use these to create a new array.

```bash
# Declare an array variable
declare -a keys

# Loop through an array, add a value to the new array using +=
for add in "${adds[@]}"; do keys+=($(bitcoin-cli -regtest getaddressinfo ${add} | jq -r .pubkey)); done
```
### Method 2
Use an index counter:
```
i=0
for el in "${adds[@]}"; do
	keys[i]=$(bitcoin-cli -regtest getaddressinfo ${el} | jq -r .pubkey)
	i=$((i+1))
done
```

Array Access
-------------
```bash
# All items in the array:
${arr[*]}

All indexes:
${!arr[*]}

# Number of items in array:
${#arr[*]}
```

Iteration
---------

```bash
nums=(1 2 3)

# Loop using indexes:
for i in ${!nums[*]}; do echo "${i}: ${nums[i]}"; done

# Loop elements directly:
for el in ${nums[*]}; do echo "${el}"; done
```

```bash
# Add to array in loop
for i in $(seq 0 2); do adds[$i]=$(bitcoin-cli -regtest getnewaddress); done

echo ${adds[@]}
```

Arrays and JSON
---------------
Use the `jq` utility to process JSON in Bash.

### Bash Array to JSON
```bash
# bash array
my_bash_array=(string1 string2 string3)

# Make a JSON representation - remaining arguments after `--args` are positional JSON text
# arguments - available to jq as `$ARGS.positional[]`. -c option gives compact (single-line) output.
jq -nc '$ARGS.positional' --args "${my_bash_array[@]}"

# Output
["string1", "string2", "string3"]
```

Resources
---------
* [Linux Journal, Bash Arrays][1]

[1]: https://www.linuxjournal.com/content/bash-arrays
