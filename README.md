# PulseLink

**PulseLink** is an asynchronous chat server built using **Boost.Asio** in C++. It supports multiple clients communicating in real-time via TCP connections. This project demonstrates the use of **asynchronous I/O** to handle multiple connections efficiently without blocking execution.

## Features
- **Multi-client support**: Handles multiple users concurrently in a single chat room.
- **Asynchronous messaging**: Uses `boost::asio::async_read` and `boost::asio::async_write` for non-blocking operations.
- **Message broadcasting**: Ensures messages from one client are delivered to all others.
- **Graceful disconnection handling**: Clients are properly removed from the chatroom when they disconnect.

## Dependencies
Ensure the following dependencies are installed:

- C++17 or later
- Boost.Asio (`libboost-dev`, `libboost-system-dev`)
- CMake (for easier compilation)

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/PulseLink.git
   cd PulseLink
   ```
2. Install Boost libraries (if not already installed):
   ```sh
   sudo apt-get install libboost-dev libboost-system-dev
   ```
3. Compile the project:
   ```sh
   g++ -std=c++17 -o server main.cpp -lboost_system -lpthread
   ```

## Usage
### Running the Server
Start the chat server by specifying a port:
```sh
./server 1234
```
This starts the server on port **1234**.

### Connecting Clients
You can connect multiple clients using **netcat** or any TCP client:
```sh
nc localhost 1234
```
Type messages and press **Enter** to send them to all connected clients.

## How It Works
1. **Server starts** and listens for incoming client connections.
2. **Client connects**, a `Session` is created, and the client joins a `Room`.
3. **Client sends messages**, which are delivered asynchronously to all participants.
4. **Client disconnects**, and they are removed from the chat room.

## Future Improvements
- Support for **multiple chat rooms**.
- **User authentication** and **message encryption**.
- WebSocket support for browser-based clients.

