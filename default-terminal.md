# Set the Default Terminal Emulator

The `update-alternatives` command creates, removes, maintains and displays information about the symbolic links comprising the Debian alternatives system.

This allows you to set the programme that opens when you trigger a default terminal (e.g. Ctrl Alt T):

```bash
sudo update-alternatives --config x-terminal-emulator 

# Output:
There are 6 choices for the alternative x-terminal-emulator (providing /usr/bin/x-terminal-emulator).

  Selection    Path                             Priority   Status
------------------------------------------------------------
  0            /usr/bin/terminator               50        auto mode
* 1            /usr/bin/gnome-terminal.wrapper   40        manual mode
  2            /usr/bin/koi8rxterm               20        manual mode
  3            /usr/bin/lxterm                   30        manual mode
  4            /usr/bin/terminator               50        manual mode
  5            /usr/bin/uxterm                   20        manual mode
  6            /usr/bin/xterm                    20        manual mode

Press <enter> to keep the current choice[*], or type selection number: 
```
