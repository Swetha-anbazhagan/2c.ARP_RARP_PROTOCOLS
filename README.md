# 2c.SIMULATING ARP /RARP PROTOCOLS
## Register Number: 212224040343
## Name : Swetha A
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
### Cilent.py
```
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; 
while True: 
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode()) 
````

### Server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP

<img width="387" height="70" alt="image" src="https://github.com/user-attachments/assets/14aa5da1-4aa8-4da0-ab3a-c36739dfb5e9" />
<img width="441" height="155" alt="image" src="https://github.com/user-attachments/assets/a8953481-c5ad-455a-9332-cb5a54a50677" />

## PROGRAM - RARP

### Cilent.py

```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```

### Server.py

```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())

```
## OUPUT -RARP
<img width="1322" height="298" alt="image" src="https://github.com/user-attachments/assets/92118529-c089-42e5-9b94-50940a9b667b" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
