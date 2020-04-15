# Arithmetic
BASH has `bc`: a language that: "...supports arbitrary precision numbers with interactive execution of statements" (From `man bc`).

```bash
# Simple:
echo "2 + 2" | bc
# Output:
4
```

Floating Point Numbers
----------------------
```bash
echo "20.211 * 2" | bc
# Output:
40.422
```

However:

```bash
echo "42/2.1" | bc
# Output:
20
```
for division, the operation becomes floor (integer) division, unless you include the standard math lib using the `-l` option for `bc`:

```bash
echo "42/20.1" | bc -l
# Output:
2.08955223880597014925
```

If you're used to Python - which is obviously super-powerful when it comes to mathematical functionality, you can run a Python command from Bash using the `-c` option:

```bash
python3 -c "print(42/20.1)"
# Output:
2.08955223880597
```

