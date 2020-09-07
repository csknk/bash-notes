# Serve Files From the Current Directory

Save the follwoing as an executable file in `$PATH`:

```bash
#!/bin/bash

# This function opens the specified URL in a new browser window of the default browser.
# If you'd rather open a new instance of firefox, replace the xdg-open call with:
# firefox --new-tab "http://0.0.0.0:$port" &
serve() {
	local port="${1:-8000}"
	xdg-open "http://127.0.0.1:$port"
	python3 -m http.server "$port" --bind 127.0.0.1
}

serve "$1"
```
The command `serve` now starts a Python3 server in the current directory and opens a new tab in the default browser.

The first command line argument allows you to specify the port on which content should be served - the default is 8000.

Tested with Ubuntu 20.04.
