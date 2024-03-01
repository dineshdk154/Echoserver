Echo server and client using python socket

# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:
@@ -20,8 +19,43 @@ Implementation using Python code
Testing the server and client 

## PROGRAM:
### SERVER CODE: echo-server.py:
```
import socket
HOST = "127.0.0.1"  # Standard loopback interface address (localhost)
PORT = 65432  # Port to listen on (non-privileged ports are > 1023)
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen()
    conn, addr = s.accept()
    with conn:
        print(f"Connected by {addr}")
        while True:
            data = conn.recv(1024)
            if not data:
                break
            conn.sendall(data)
```

### CLIENT CODE: echo-client.py:
```
import socket
HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Hello, world")
    data = s.recv(1024)
print(f"Received {data!r}")
```

## OUTPUT:
### SERVER OUTPUT:
![image](https://github.com/dineshdk154/Echoserver/assets/104413084/4e60cba7-9af1-490a-b0fb-aed4be0846df)


### CLIENT SIDE:
![Screenshot 2024-03-01 105600](https://github.com/dineshdk154/Echoserver/assets/104413084/8395c26b-1520-49df-8a12-a6152e975502)



## RESULT:
The program is executed successfully
