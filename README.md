# EXPERIMENT 4.:EXECUTION OF NETWORK COMMANDS
## NAME : SHREYESHKAR SEKAR 
## REGISTRATION NUMBER : 212224220099
## AIM :
Use of Network commands in Real Time environment
## Software :
Command Prompt And Network Protocol Analyzer
## Procedure: 
To do this EXPERIMENT- follows these steps:
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

## PROGRAM :

### SERVER SIDE : 
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
    while True:
        ip= input("Enter Website u want to ping :")
        s.send(ip.encode())
        response=s.recv(1024).decode()
        if response:
            print ("Ping result :",response)
        else:
            print ("No response from server")
except Exception as e:
    print ("Error:", e)
finally:
    s.close()
```
### CLIENT SIDE :
```
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
while True:
    c,addr=s.accept()
    print("Connecting from ",addr)
    try:
        hostname=c.recv(1024).decode().strip()
        if hostname:
            try:
                response=str(ping(hostname,verbose=True))
                c.send(response.encode())
            except Exception as e:
                c.send("ping failed  {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error: ",e)
    finally:
        c.close()
```
### TRACEROUTE COMMAND :
```
import subprocess

def traceroute(host):
    print(f"Tracing route to {host}\n")
    result = subprocess.run(["tracert", host], text=True, capture_output=True)
    print(result.stdout)

traceroute("www.google.com")


```

## Output
<img width="1572" height="1090" alt="4 server and clin" src="https://github.com/user-attachments/assets/6a45cb4f-57cc-4a66-8b2b-bf9a4b63b8d4" />

<img width="908" height="1067" alt="4tracerout" src="https://github.com/user-attachments/assets/24be8e33-e12f-4b21-a2c5-131fab151429" />



## Result
Thus Execution of Network commands Performed 
