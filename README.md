# 🧠 System Programming Final Project – Multithreaded Shortest Path Server & Client (C++)

This project implements a **multithreaded server** and a **client** in **C++** for computing the **shortest path** between two nodes in an undirected graph. The server handles each client request in a separate thread and communicates using TCP sockets. It also implements a caching mechanism for better performance.

---
## 🖥️ Server

### 🔧 How to Run

./a.out <graph_file> <port>

<graph_file> – path to a text file describing the undirected graph.

<port> – port number to listen on.


 Graph File Format
Each line in the file represents a bidirectional edge in the graph:
<node1> <node2>

# 🧩 Server Features
Parses a graph from the file into an adjacency list.

Accepts TCP connections from multiple clients using POSIX sockets.

Each client is handled in a separate thread using pthread.

Computes shortest path using BFS.

Caches the last 10 queries and results.

Responses are returned as a string like:

0 -> 1 -> 2 -> 3

# Client
🔧 How to Run
./a.out <server_ip> <port> <start_node> <end_node>

<server_ip> – the server's IP address (e.g. 127.0.0.1).

<port> – the port number the server is listening on.

<start_node> and <end_node> – node IDs to query the shortest path between.

🧾 Example:
Server terminal
./a.out db.csv 4444

Client terminal
./a.out 127.0.0.1 4444 0 19382

🖨️ Expected Output
The shortest path between the nodes (if it exists), e.g.:

0 -> 18427 -> 19382

If no path exists:
Not Exist

# Compilation:
g++ *.cpp

# 🧠 Implementation Details
Sockets: AF_INET, SOCK_STREAM

Threading: pthread_create, one thread per client

Graph: unordered_map<string, vector<string>>

Cache: stores last 10 Path_ structs with start, end, and computed path


