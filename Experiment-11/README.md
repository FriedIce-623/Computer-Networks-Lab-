# Experiment 11: Study of Socket Programming and Client-Server Model

## Aim
To study socket programming and implement communication between a client and a server using Python.

## Requirements
- Windows 10/11
- Python 3
- VS Code or any Python editor
- Command Prompt / Terminal

## Theory

Socket programming enables two programs to communicate over a network.

The client-server model consists of:
- **Client:** Initiates communication by sending requests.
- **Server:** Waits for client connections and responds to requests.
- **Socket:** Endpoint used for communication.

TCP is a connection-oriented protocol that provides reliable data transmission.

## Procedure

1. Create two Python files: `server.py` and `client.py`.
2. Write the server program using the socket module.
3. Create a TCP socket using `socket.socket(socket.AF_INET, socket.SOCK_STREAM)`.
4. Bind the server to IP address `127.0.0.1` and port `5000`.
5. Start listening for incoming connections using `listen()`.
6. Accept a client connection using `accept()`.
7. Write the client program and connect it to the server using `connect()`.
8. Send a message from the client using `send()`.
9. Receive the message on the server using `recv()`.
10. Send a response from the server to the client.
11. Close both sockets.

## Server Program

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(("127.0.0.1", 5000))
server.listen(1)

print("Server is waiting for a connection...")

conn, addr = server.accept()
print("Connected to:", addr)

message = conn.recv(1024).decode()
print("Client says:", message)

conn.send("Hello from Server!".encode())

conn.close()
server.close()
```

## Client Program

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(("127.0.0.1", 5000))

client.send("Hello from Client!".encode())

message = client.recv(1024).decode()
print("Server says:", message)

client.close()
```

## Execution

1. Run `python server.py` in the first terminal.
2. Run `python client.py` in the second terminal.
3. Observe the messages exchanged between the client and server.

## Observations
- The server waits for incoming client connections.
- The client establishes a TCP connection with the server.
- The client sends a message to the server.
- The server receives the message and sends a response.
- Both programs close their sockets after communication.

## Result
Successfully implemented client-server communication using TCP socket programming in Python.

## Viva Questions

1. What is socket programming?
2. What is a socket?
3. What is the client-server model?
4. What is the difference between a client and a server?
5. What is TCP?
6. What is UDP?
7. What is the purpose of the bind() function?
8. What does listen() do?
9. What is the purpose of accept()?
10. What is the difference between send() and recv()?
11. What is localhost?
12. What is a port number?
13. What is AF_INET?
14. What is SOCK_STREAM?
15. Why do we close a socket after communication?
