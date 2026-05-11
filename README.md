# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

## SERVER SIDE
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```

## CLIENT SIDE
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT


## SERVER SIDE
<img width="1119" height="218" alt="image" src="https://github.com/user-attachments/assets/0849a620-b9c5-4807-844c-5b7608a01dc8" />





## CLIENT SIDE
<img width="1114" height="266" alt="image" src="https://github.com/user-attachments/assets/70ad3479-4397-46ad-8248-7967e78250c9" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
