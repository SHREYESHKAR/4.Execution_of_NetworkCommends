# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

### Client.py
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

c, addr = s.accept()
print("Connected to:", addr)

while True:
    hostname = c.recv(1024).decode()
    try:
        result = ping(hostname, count=2, verbose=False)
        c.send(str(result).encode())
    except Exception as e:
        c.send(f"Error: {str(e)}".encode())
```
### server.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping: ")
    s.send(ip.encode())
    print(s.recv(1024).decode())
```
## Output
<img width="1610" height="266" alt="image" src="https://github.com/user-attachments/assets/6d27e9b0-d6ad-4e80-8e30-fbf385361f2c" />

## Result
Thus Execution of Network commands Performed # 4.Execution_of_NetworkCommands
