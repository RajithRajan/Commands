### net
To list all the network drive with server mapping
```
net use 
```
List all the access in current domain
```
net user <id> /domain
```
List users who belong to a group
```
net group <group_name> /domain
```

### netsh
_To proxy to a ip address and port_  

```
netsh interface portproxy add v4tov4 listenport=<port-to-listen> listenaddress=0.0.0.0 connectport=<port-to-forward> connectaddress=<forward-to-this-IP-address>
```

eg to proxy to natted WSL 3000 port  

```
netsh interface portproxy add v4tov4 listenport=3000 listenaddress=0.0.0.0 connectport=3000 connectaddress=172.30.16.3
```

To open firewall to accept connection on 5000 port  

```
netsh advfirewall firewall add rule name="Allowing LAN connections" dir=in action=allow protocol=TCP localport=5000
```

To list all the active portproxy

```
netsh interface portproxy show all
```
To remove an entry of port proxy
```
netsh interface portproxy delete v4tov4 listenport=4422 listenaddress=192.168.1.111
```

### netstat
To list all the active connections
```
netstat -a
```
To get all the active fileshare
```
netstat -ano -p TCP | Find "445"
```
To find listners on 8080
```
netstat -aof | findstr :8080
```

### nslookup
To find dns record information
```
nslookup <ipaddress>
```

### ping
To check the connectivity to remote server, it works only if ICMP protocol is open.
```
ping <ip_address
```

### tasklist
To list all tasks
```
tasklist
```
To list a specific process id
```
Tasklist | Find "2196"
```
```
Tasklist /fi "pid EQ 2216"
```

### telnet
To check if network connectivity if open to server at specific port. Listner should be running at the port to accept connection.
```
telnet <ip> <port>
```

### Tracert
Trace route a package takes to reach destination. Its limited by networking allowing tracing.
```
Tracert www.google.com
```



To search AD group & users against domain controller
%SystemRoot%\SYSTEM32\rundll32.exe dsquery,OpenQueryWindow
