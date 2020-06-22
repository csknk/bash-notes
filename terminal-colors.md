# Set Terminal Colours

```bash
#!/bin/bash

# Set colors
BLUE=$(tput setaf 4)
RED=$(tput setaf 1)
REDBOLD=$(tput setaf 1; tput bold)
GREEN=$(tput setaf 2)
BLACK=$(tput setaf 0)
BOLD=$(tput bold)
STANDOUT=$(tput smso)
YELLOW=$(tput setaf 2)
YELLOWBG=$(tput smso; tput setaf 2)
NC=$(tput sgr0)

echo "${YELLOWBG}yellow ${NC}"
echo "${YELLOW}yellow ${NC}"
echo "${BOLD}${YELLOW}yellow ${NC}"
echo "${RED}red ${NC}"
echo "${STANDOUT}${RED}red ${NC}"
echo "${REDBOLD}red bold${NC}"
echo "${GREEN}green${NC}"
echo "${BOLD}${GREEN}green${NC}"
echo "${STANDOUT}${BOLD}${GREEN}green${NC}"
echo "${STANDOUT}${GREEN}green${NC}"
echo "${BLUE}blue${NC}"
echo "${STANDOUT}${BLUE}blue${NC}"
echo "normal"
```
