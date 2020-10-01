# BASH Arrays

Define an array by enclosing elements in parenthesis:

```bash
arr=(1 2 3)
```

Array access:
```bash
# All items in the array:
${arr[*]}

All indexes:
${!arr[*]}

# Number of items in array:
${#arr[*]}
```

### Iteration

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

Resources
---------
* [Linux Journal, Bash Arrays][1]

[1]: https://www.linuxjournal.com/content/bash-arrays
