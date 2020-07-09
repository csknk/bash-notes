# Virtual Machines

Notes on using KVM virtual machines.

Serve Files From Guest to Host
------------------------------

### On Guest
Move into the directory that you want to serve.

Determine the LAN IP address for the guest:

```
hostname -I
```

Run a simple python server bound to this host:

```
python3 -m http.server --bind 192.168.100.10 8888

# Binds current directory to http://192.168.100.10:8888
# Alternatively:

python3 -m http.server --bind $(hostname -I) 8888
```

### On Host

Browse to the guests host:port combination (in this case http://192.168.100.10:8888) and download files as needed.

Alternatively, use `wget` or `curl`:

```bash
wget http://192.168.100.10:8888/my-file.txt
```

Rsync From Host to Guest Using SSH
----------------------------------
Assumes SSH has been setup, and that OpenSSH server is running on the guest. See [reference][1] for installation/setup of OpenSSH on Ubuntu.

```bash
# Replace `user` with your username
rsync -ravz --progress user@192.168.100.10:/path/to/files/ /path/to/host/dir

# To current directory
rsync -ravz --progress user@192.168.100.10:/path/to/files/ .

# As above but create the `files` directory:
rsync -ravz --progress user@192.168.100.10:/path/to/files .
```
References
----------
* [OpenSSH Setup on Ubuntu][1]

[1]: https://ubuntu.com/server/docs/service-openssh
