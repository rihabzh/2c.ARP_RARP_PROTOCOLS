# 2c.SIMULATING ARP /RARP PROTOCOLS
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
# server:
```
import socket

s = socket.socket()
s.bind(("localhost", 8000))
s.listen(1)

table = {
    "192.168.1.1": "AA:BB:CC",
    "192.168.1.2": "DD:EE:FF"
}

c, addr = s.accept()

while True:
    ip = c.recv(1024).decode()
    
    if ip in table:
        c.send(table[ip].encode())
    else:
        c.send("IP not found".encode())
```
# client :
```
import socket

s = socket.socket()
s.connect(("localhost", 8000))

while True:
    ip = input("Enter IP address: ")
    s.send(ip.encode())
    
    mac = s.recv(1024).decode()
    print("MAC Address:", mac)
```
## OUPUT - ARP


## PROGRAM - RARP

## OUPUT -RARP
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
