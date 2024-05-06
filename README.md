# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name:Vedagiri Indu Sree
## Reg No:212223230236
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
## Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
## Server:
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter logical address: ")
s.send(ip.encode())
print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
## Client:
![image](https://github.com/vedagiriindusree/2c.ARP_RARP_PROTOCOLS/assets/149366776/5b0f1ce3-0002-4b91-a04b-cbef380bdd4c)
## Server:
![image](https://github.com/vedagiriindusree/2c.ARP_RARP_PROTOCOLS/assets/149366776/13ff7f3b-69dd-47f1-9382-4219001dab04)
## PROGRAM - RARP
## Client:
```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr = s.accept()
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}
while True:
ip = c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
## Server:
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter MAC address: ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
## Client:
![image](https://github.com/vedagiriindusree/2c.ARP_RARP_PROTOCOLS/assets/149366776/423f8cd5-b9a0-4a05-abb0-6cd95b1de97f)
## Server:
![image](https://github.com/vedagiriindusree/2c.ARP_RARP_PROTOCOLS/assets/149366776/a5af204c-f34e-483f-b9fe-f7982f60c426)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
