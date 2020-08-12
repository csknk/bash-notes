Make a Temporary Directory
==========================

Useful for experiments where you don't care if your work is lost on a reboot:

```bash
# Make a temporary directory and move into it:
cd $(mktemp -d)
```
