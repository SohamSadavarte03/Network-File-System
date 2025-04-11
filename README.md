# 📁 Distributed File System

This project consists of a **Naming Server**, multiple **Storage Servers**, and a **Client** that interact over TCP to perform operations such as creating, reading, writing, streaming, and deleting files.

---

## 📦 Files

- `naming.c` – Naming server handling metadata and routing.
- `storage.c` – Storage server managing file content and directory operations.
- `client.c` – Client interface for interacting with the distributed system.

---

## ⚙️ Requirements

- GCC (GNU Compiler)
- Linux/Unix environment
- `mpv` (for audio streaming playback)
- `pthread` library

Install `mpv` if it's not already installed:
```bash
sudo apt install mpv
```

---

## 🔨 Compilation

You can compile each component using `gcc`. Open three separate terminals for the three components and compile as follows:

### 1. Naming Server
```bash
gcc naming.c -o naming_server -lpthread
```

### 2. Storage Server
```bash
gcc storage.c -o storage_server -lpthread
```

### 3. Client
```bash
gcc client.c -o client -lpthread
```

---

## 🚀 Running the System

### 1. Start the Naming Server
In **Terminal 1**:
```bash
./naming_server
```

### 2. Start One or More Storage Servers
In **Terminal 2 and 3**, run storage servers with different ports:
```bash
./storage_server <naming_server_ip> <naming_server_port> <storage_server_port> <storage_dir>
```

For example:
```bash
./storage_server 127.0.0.1 8090 9090 ./storage1
./storage_server 127.0.0.1 8090 9091 ./storage2
```

> Note: `storage.c` should be modified to read these arguments in `main()` if not already done.

### 3. Start the Client
In **Terminal 4**:
```bash
./client
```

Follow the interactive prompts to:
- READ files
- WRITE data
- STREAM audio files
- CREATE directory/file
- DELETE files/directories
- EXIT

---

## 💡 Example Commands

When prompted in the client:

```bash
Enter command (READ/WRITE/INFO/STREAM/EXIT): WRITE
Enter file path: /songs/demo.txt
Do you want to write synchronously irrespective of time overhead? (yes/no): no
Enter data to write: Hello World!
```

---

## 📌 Notes

- Ensure all server ports are open or allowed through the firewall.
- Make sure all directories passed as `storage_dir` exist or will be created by the storage server.
- The system supports async and sync file writes and streaming using `mpv`.
- Log files like `naming_server.log` will be generated.

---

## 🧼 Cleanup

To remove executables:
```bash
rm naming_server storage_server client
```

