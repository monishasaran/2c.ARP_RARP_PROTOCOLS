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
SERVER:
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
```

CLIENT:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP:
CLIENT:

<img width="757" height="200" alt="Screenshot 2026-05-15 140905" src="https://github.com/user-attachments/assets/0e027e72-09b5-460e-8edd-f4e07671dd19" />

SERVER:

<img width="808" height="252" alt="Screenshot 2026-05-15 140846" src="https://github.com/user-attachments/assets/7e258725-112c-4cd9-b97c-3e85a5897e31" />



## PROGRAM - RARP:
SERVER:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
CLIENT:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
ip=input("Enter MAC Address : ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP:
CLIENT:

<img width="778" height="224" alt="Screenshot 2026-05-15 142113" src="https://github.com/user-attachments/assets/73377434-d3b5-4940-82e4-6d3819af038b" />

SERVER:

<img width="745" height="191" alt="Screenshot 2026-05-15 142122" src="https://github.com/user-attachments/assets/29655df8-45d6-4bba-90d5-8e003e00972e" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
