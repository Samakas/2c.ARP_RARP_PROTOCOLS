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
### Client
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
### Server
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
### Client
![client2c](https://github.com/Samakas/2c.ARP_RARP_PROTOCOLS/assets/154731670/b4235596-7fe6-4b2b-a4b8-aaa3dcb4b5e6)
### Server
![serever2c](https://github.com/Samakas/2c.ARP_RARP_PROTOCOLS/assets/154731670/84ad61a6-4e36-4acc-9fd4-a6f53c88edb1)

## PROGRAM - RARP
### Client
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
### Server
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
### Client
![client2crp](https://github.com/Samakas/2c.ARP_RARP_PROTOCOLS/assets/154731670/311083b7-64b6-43da-812f-cc92249e4cd4)
### Server
![server2crp](https://github.com/Samakas/2c.ARP_RARP_PROTOCOLS/assets/154731670/025c053b-767e-4f4d-813e-5243a320daad)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
