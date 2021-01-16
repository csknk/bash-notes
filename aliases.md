#Aliases

To use literal single quotes in an alias, use the `$''` quoting form:

```bash
# Alias that outputs the number of connected inbound nodes
alias btc-n-inbound=$'echo "$(bitcoin-cli getpeerinfo | jq \'.[] | select(.inbound | select(true)) | .id\' | wc -l) inbound nodes connected"'
```
