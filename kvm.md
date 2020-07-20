# KVM/QEMU Commands

The command line utility used to manage Kernel Virtual Machines is `virsh`. This tool can be used to manage guest domains: create, pause, start and shutdown domains.

Determine IP Addresses of Running Guests
----------------------------------------

```bash
virsh net-list
# Output:
 Name      State    Autostart   Persistent
--------------------------------------------
 default   active   yes         yes
 intnet1   active   yes         yes
 intnet2   active   yes         yes

virsh net-info default
# Output:
Name:           default
UUID:           db495f4f-07b2-4b2a-bd75-823523b72f37
Active:         yes
Persistent:     yes
Autostart:      yes
Bridge:         virbr0


virsh net-dhcp-leases default
# Output:
 Expiry Time           MAC address         Protocol   IP address           Hostname   Client ID or DUID
---------------------------------------------------------------------------------------------------------
 2020-07-20 20:37:47   52:54:00:27:61:77   ipv4       192.168.123.204/24   donnager   -

# One liner - if you know an identifier for the vm:
virsh net-dhcp-leases default | grep donnager | awk '{print $5}' | awk -F / '{print $1}'
```
You can now SSH into the vm: `ssh user@192.168.123.204`

Alternative, if you know the domain name:

```bash
virsh domifaddr donnager
```

Virsh REPL
----------
You can enter a virsh shell by entering `virsh` in the terminal. Once in the interactive terminal, you can run commands wihtout the `virsh` command:

```bash
Welcome to virsh, the virtualization interactive terminal.

Type:  'help' for help with commands
       'quit' to quit

virsh # start goldfish
Domain goldfish started

virsh # shutdown goldfish
Domain goldfish is being shutdown

```

To quit the interative terminal enter `quit`.

Handy Commands
--------------

### start
The `start` command starts a previously defined but inactive domain. Specify a domain name or a UUID.

### shutdown
The `shutdown` command gracefully shuts down a running domain, coordinated with the domain OS.
