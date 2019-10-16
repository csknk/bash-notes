Looping in Bash
===============

Nested For Loop
---------------
```bash
# One liner to create 10 files, each file with 25 lines
# Semicolons are required!
for i in {1..10}; do for j in {1..25}; do echo "line ${j}" >> file-${i}.txt; done; done
```
