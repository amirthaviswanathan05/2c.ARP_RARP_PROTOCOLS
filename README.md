# 2c.SIMULATING ARP /RARP PROTOCOLS
# Name: AMIRTHAVARSHINI V
# Register Number: 212223040014

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
CLIENT:
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
SERVER:
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
CLIENT:

![372314081-97351268-34eb-481d-a2d6-6262212341dc](https://github.com/user-attachments/assets/82cc62df-2323-45c9-9df1-0e2a6ecfa504)

SERVER:

![372314199-8600f587-c9bb-4ca4-ae6d-027eea53d355](https://github.com/user-attachments/assets/892ca81b-89cf-4539-8a35-de73e023a682)

## PROGRAM - RARP
CLIENT:
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

SERVER:
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
CLIENT:

![372314330-a738ebb4-7dd0-407e-82f6-9c89ad443fcc](https://github.com/user-attachments/assets/25a69195-101a-492a-91eb-84a333f07fba)

SERVER:

![372314372-cbfa62ca-6eca-4e74-8212-2352be575b6e](https://github.com/user-attachments/assets/c7f5be6f-eb82-4b72-8156-eeca19969e64)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
