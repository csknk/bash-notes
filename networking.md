# Networking

Get the external IP using an external service - this is necessary if behind a `NAT`:

```bash
curl https://ipinfo.io/ip

# Different service, wget not curl, same result:
wget -qO- https://ipecho.net/plain ; echo

# ipecho.net service with better output format (terminating newline):
curl https://ipecho.net/plain ; echo

# Assign external IP to a Bash variable:
MYIP=$(curl https://ipecho.net/plain)
```
