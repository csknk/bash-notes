Sudo Tips
=========

Grant a user the authority to run a sudo-restricted command without entering a password:

```bash
sudo visudo

# At end of file enter:
# <username> ALL-NOPASSWD: <command 1> <command2> <...>
# For example:

john ALL=NOPASSWD: /sbin/poweroff, /sbin/reboot
```
User `john` can now trigger a reboot or poweroff by entering the relevant command - they will not be prompted for a password.

From `man sudoers`:

PASSWD and NOPASSWD
By default, sudo requires that a user authenticate him or herself before running a command.  This behavior can be modified via the NOPASSWD tag.  Like a Runas_Spec, the NOPASSWD tag sets a default for the commands that follow it in the Cmnd_Spec_List.  Conversely, the PASSWD tag can be used to reverse things. For example:

```
ray     rushmore = NOPASSWD: /bin/kill, /bin/ls, /usr/bin/lprm
```
would allow the user ray to run /bin/kill, /bin/ls, and /usr/bin/lprm as root on the machine rushmore
without authenticating himself.  If we only want ray to be able to run /bin/kill without a password the entry would be:

```
ray     rushmore = NOPASSWD: /bin/kill, PASSWD: /bin/ls, /usr/bin/lprm
```

Note, however, that the PASSWD tag has no effect on users who are in the group specified by the exempt_group option. 

By default, if the NOPASSWD tag is applied to any of the entries for a user on the current host, he or she will be able to run “sudo -l” without a password.  Additionally, a user may only run “sudo -v” without a password if the NOPASSWD tag is present for all a user's entries that pertain to the current host. This behavior may be overridden via the verifypw and listpw options.

---
