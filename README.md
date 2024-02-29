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
![image](https://github.com/pradeepasri26/Echoserver/assets/131433142/a89b0d25-0b41-4b95-9eeb-9c7f6ed92533)

### CLIENT SIDE:
![image](https://github.com/pradeepasri26/Echoserver/assets/131433142/802600e0-45fe-4a33-9388-e123fbdc7087)


## RESULT:
The program is executed successfully
