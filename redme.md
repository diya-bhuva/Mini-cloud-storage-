⭐ Mini Cloud Storage System

A simple client–server cloud storage application built using C, TCP Socket Programming, and POSIX File System APIs.
The project allows users to upload, download, and manage files on a remote server—similar to how cloud services like Google Drive or Dropbox work at a basic level.
📌 Features
🔹 Client Features

Connects to the cloud server using TCP

Supports commands:
help – list all available commands
upload <filename> – upload a file to the server
download <filename> – download a file from the server
bye – disconnect safely

🔹 Server Features
Accepts client connections
Creates a user-specific storage folder (e.g., client_<id>)
Receives files from clients
Sends files back to clients on request
Handles missing files and invalid commands gracefully

🧠 Topics Used (System Programming Concepts)
This project demonstrates key concepts from computer systems and OS programming:

✔ Socket Programming
socket(), bind(), listen(), accept(), connect()
send() / recv()

✔ Client–Server Architecture
Persistent server
Request/response protocol design

✔ File Handling
fopen() / fread() / fwrite()
stat() for file size
Directory creation with mkdir()

✔ POSIX System Calls
Directory and filesystem operations
Handling large file transfers in chunks

✔ Buffers & Memory Management
Using 1024-byte data buffers for efficient transfer

⚙️ How to Compile

We use GCC.

Compile the server
gcc server.c -o server

Compile the client
gcc client.c -o client

🚀 How to Run

1. Start the server
./server
The server will start listening on port 8888
and automatically create client_<id> folders when clients connect.

2. Start the client
./client
You will be prompted to enter the server IP (e.g., 127.0.0.1 for localhost).

📝 Client Commands
Command	Description
help	Shows all available commands
upload <filename>	Upload a file to your cloud folder
download <filename>	Download a file from the server
bye	Disconnect safely

📤 File Upload Process
Client sends upload command
Client sends filename
Server checks for duplicates
Client sends file size
Client sends file data in chunks
Server stores file in client_<id> folder
Server returns OK

📥 File Download Process
Client sends download command
Client sends filename
Server checks if file exists
Server sends file size
Server sends file data
Client writes the file locally

🛑 Error Handling
The system detects:
Missing files
Invalid commands
Transmission failures
Directory creation issues
Zero-byte files
Overwriting existing files

All errors are sent to the client in simple messages like:
ERROR
NOT_FOUND
DUPLICATE
INVALID

