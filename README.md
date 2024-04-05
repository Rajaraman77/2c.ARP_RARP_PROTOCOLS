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
## client:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"165.165.79.1"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT - ARP
## client:
![image](https://github.com/Rajaraman77/2c.ARP_RARP_PROTOCOLS/assets/150319383/3e6e6a0b-cbbf-41c3-be58-624841309097)
## server:
![image](https://github.com/Rajaraman77/2c.ARP_RARP_PROTOCOLS/assets/150319383/7eef4880-3d75-4dfb-8db4-3d6e985906fe)

## PROGRAM - RARP
## client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("not found".encode())
```
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("enter logical address:")
    s.send(ip.encode())
    print("mac address",s.recv(1024).decode())
```
## OUPUT -RARP
## client:
![image](https://github.com/Rajaraman77/2c.ARP_RARP_PROTOCOLS/assets/150319383/4f278da8-51fe-46a6-b10c-e17cb5b83b9a)
## server:
![image](https://github.com/Rajaraman77/2c.ARP_RARP_PROTOCOLS/assets/150319383/874d84ba-4b07-4aab-b2c8-163afe83ab2a)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
