Test Local Ports with Telnet
============================

Connect to a local port using Telnet:

```bash
telnet localhost 8001

# If connected:
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
```
Once you are connected, you can send data to the port. For example:

```
# Request:
GET / HTTP/1.1

# Response:
HTTP/1.1 200 OK
Content-Type:text/html
Content-Length: 618
Server: David's C HTTP Server
Connection: close

<!DOCTYPE html>
<html>
	<head>
...
```
