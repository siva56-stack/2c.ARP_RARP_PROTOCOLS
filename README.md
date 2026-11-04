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
```python
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("ARP Server is listening...")
c, addr = s.accept()

address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = c.recv(1024).decode()
    print(f"Received IP: {ip}")
    mac = address.get(ip, "Not Found")
    c.send(mac.encode())
```
## OUPUT - ARP
<img width="1183" height="146" alt="Screenshot 2026-11-04 110335" src="https://github.com/user-attachments/assets/d4d06175-6167-4628-9ad2-8450d6a036ef" />

## PROGRAM - RARP
```python
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter IP Address: ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```
## OUPUT -RARP
<img width="1187" height="173" alt="Screenshot 2026-11-04 110355" src="https://github.com/user-attachments/assets/7dfa86ab-ce0f-4bee-a962-dd91d5f0d652" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
