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
# SERVER
    import socket
    
    # Create socket
    s = socket.socket()
    
    # Bind host and port
    s.bind(('localhost', 8000))
    s.listen(5)
    
    # Accept connection
    c, addr = s.accept()
    
    # IP address and MAC address mapping
    address = {
        "165.165.80.80": "6A:08:AA:C2",
        "165.165.79.1": "8A:BC:E3:FA"
    }
    
    while True:
        # Receive IP address
        ip = c.recv(1024).decode()
    
        try:
            # Send corresponding MAC address
            c.send(address[ip].encode())
    
        except KeyError:
            c.send("Not Found".encode())

# CLIENT

    import socket
    
    # Create socket
    s = socket.socket()
    
    # Connect to server
    s.connect(('localhost', 8000))
    
    while True:
        # Enter IP address
        ip = input("Enter logical Address : ")
    
        # Send IP address to server
        s.send(ip.encode())
    
        # Receive MAC address
        print("MAC Address", s.recv(1024).decode())



## OUPUT - ARP
<img width="1138" height="389" alt="Screenshot 2026-11-17 at 4 08 51 PM" src="https://github.com/user-attachments/assets/57f3fbaf-4f39-4fc6-bd81-8c766da35fde" />



## PROGRAM - RARP
# SERVER
    
    import socket
    
    # Create socket
    s = socket.socket()
    
    # Bind host and port
    s.bind(('localhost', 9000))
    s.listen(5)
    
    # Accept connection
    c, addr = s.accept()
    
    # MAC address and IP address mapping
    address = {
        "6A:08:AA:C2": "192.168.1.100",
        "8A:BC:E3:FA": "192.168.1.99"
    }
    
    while True:
        # Receive MAC address
        ip = c.recv(1024).decode()
    
        try:
            # Send corresponding IP address
            c.send(address[ip].encode())
    
        except KeyError:
            c.send("Not Found".encode())



# CLIENT
    import socket
    
    # Create socket
    s = socket.socket()
    
    # Connect to server
    s.connect(('localhost', 9000))
    
    while True:
        # Enter MAC address
        ip = input("Enter MAC Address : ")
    
        # Send MAC address to server
        s.send(ip.encode())
    
        # Receive logical address
        print("Logical Address", s.recv(1024).decode())


## OUPUT -RARP
<img width="1139" height="398" alt="Screenshot 2026-11-17 at 4 10 38 PM" src="https://github.com/user-attachments/assets/9db3c7cc-bd3b-49d6-a2fc-702441a1f6c1" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
