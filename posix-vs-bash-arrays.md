# Posix Vs Bash Arrays

There are no arrays in Posix shells, so you may have to get creative.

Get an Element from a Bash Array
--------------------------------

```bash

#!/bin/bash

# IPV4: 024b9a1fa8e006f1e3937f65f66c408e6da8e1ca728ea43222a7381df1cc449605@128.199.202.168
# IPV4: 0204a2b95b4c208383d7f02e741a8bfd5b5b7e8bea8d1543b1255da8342d9f2c6b@172.81.178.189
# IPV4: 020ca546d600037181b7cbcd094818100d780d32fd9f210e14390e0d10b7ec71fb@187.65.218.133
# IPV4: 0216006237022044d9bdb73ca51af267c5f67cf76095b4c6275f1162eb422fed68@108.7.50.215
# IPV4: 0219fc8bad855d3c861166a89d637950242230fd3d475bb4a2d1da8c89b97beb0a@78.94.255.174
# IPV4: 024b00cf3368dbff39daa6de5638cd877b96227066e1e0d31b10183daa63ac325d@94.156.174.22
# IPV4: 0260fab633066ed7b1d9b9b8a0fac87e1579d1709e874d28a0d171a1f5c43bb877@54.245.57.153
# IPV4: 027cb5b394c5330467081901dba14d48a4ac0f10012e5791e725a65d326405a82e@82.40.164.125
# IPV4: 02827a7ba367d10a29f0a178be878f737292889d1926b40301780d7e1402a90a72@18.223.138.245
# IPV4: 02866bd9513e4e82f250c9b8a0b83cabc9be3c4824f7016bd160859d0fad3d8920@153.126.136.98
# IPV4: 029d50d59c78b81a39f4ca40b6bc9b89710542a31429b69aa075b91b587979205d@185.228.137.238

# Make an array from the data shown above.
mapfile -t RECORDS < <(grep '^# IPV4:' "$0")
N_RECORDS=${#RECORDS[@]}
max_idx=$(( N_RECORDS - 1 ))

echo "Select a record in the range [0 .. $max_idx]"
while read -r index && [[ ${index} -lt 0 ]] || [[ ${index} -gt ${max_idx} ]]; do
	echo "Please enter a number in the required range."
done

echo "${RECORDS[${index}]}"
```
Posix
-----
Achieve a similar effect by retrieving a specific record from a newline delimted string using `head` and `tail` commands.

```sh
N_RECORDS=$(grep -c '^# IPV4:' "$0")
RECORDS=$(grep '^# IPV4:' "$0") 

echo "Enter index in range [1 .. ${N_RECORDS}]"
while read -r idx && [ "$idx" -le 0 ] || [ "$idx" -gt "${N_RECORDS}" ]; do
      echo "Please enter a number in the required range:"
done      

RECORD=$(echo "${RECORDS}" | head -n "$idx" | tail -n 1 | cut -d' ' -f3-)
echo "${RECORD}"
```

