# Java Chat Application

A real-time client-server chat application built in Java featuring file sharing capabilities, and sound notifications. This application demonstrates advanced Java networking, GUI development, and multi-threading concepts.

![Java](https://img.shields.io/badge/Java-17-orange)
![Swing](https://img.shields.io/badge/Swing-GUI-blue)
![Sockets](https://img.shields.io/badge/Sockets-Networking-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

## Features

### Real-time Messaging
- Instant text communication 
- Message timestamps and user avatars
- Auto-scroll to latest messages
- HTML/CSS styled chat interface

### File Transfer
- Send and receive any file type
- Automatic file size formatting (B, KB, MB, GB)
- Progress indication and confirmation
- Files automatically saved to Downloads folder

### Sound Notifications
- Audio alerts for incoming messages
- Audio alerts for file transfers
- Non-blocking notification system

### UI Design
- Gradient backgrounds and smooth animations
- Professional color scheme
- Responsive layout with proper spacing
- Segoe UI font for modern appearance

### Thread Safe Architecture
- Proper multi-threading with EDT handling
- Non-blocking I/O operations
- Connection status indicators
- Error handling and user feedback

## Quick Start

### Prerequisites
- Java 17 or higher (Eclipse Adoptium JDK recommended)
- Windows/Linux/Mac OS

### Installation

1. Clone or download the project files
2. Navigate to the project directory:
   ```bash
   cd ClientServerChat
   ```

3. Compile the application:
   ```bash
   javac -d build/classes src/clientserverchat/*.java
   ```

### Running the Application

Step 1: Start the Server
```bash
java -cp build/classes clientserverchat.ServerForm
```
The server window will open and show "Waiting for client..."

Step 2: Start the Client
```bash
java -cp build/classes clientserverchat.ClientForm
```
The client window will open and show "Connecting..." then "Connected"

Step 3: Chat!
- Type messages and press SEND or Enter
- Click File to send files
- Both windows will show messages and play notification sounds

## Usage Guide


### Connection Status
- Server: Shows "Waiting for client..." → "Connected"
- Client: Shows "Connecting..." → "Connected"
- Input fields and buttons are disabled until connected

## Project Structure

```
ClientServerChat/
├── src/
│   └── clientserverchat/
│       ├── ClientForm.java      # Client GUI and connection logic
│       ├── ServerForm.java      # Server GUI and connection logic
│       ├── ClientForm.form      # NetBeans GUI designer files
│       ├── ServerForm.form
│       └── ClientServerChat.java # Main class (if used)
├── build/
│   └── classes/                 # Compiled .class files
├── build.xml                    # Ant build script
├── manifest.mf                  # JAR manifest
├── nbproject/                   # NetBeans project files
└── README.md                    # This file
```

## Technical Details

### Architecture
- Client-Server Model: Traditional socket-based communication
- Port: 1201 (hardcoded, localhost only)
- Protocol: UTF-8 strings for messages, binary for files

### Key Technologies
- Java Swing: GUI framework with JEditorPane for HTML rendering
- Java Sockets: ServerSocket and Socket for network communication
- Java Sound API: Audio notifications
- NIO.2: Modern file operations
- Multi-threading: Background threads for I/O operations

### Message Format
- Text Messages: Plain UTF-8 strings
- File Transfers: "FILE:filename:size" header followed by binary data
- HTML Rendering: CSS-styled message bubbles in JEditorPane

### Threading Model
- Main Thread: UI updates and user interactions
- Connection Thread: Socket establishment and I/O
- EDT: Event Dispatch Thread for Swing updates
- File Transfer Thread: Background file operations


## 🔧 Development

### Building from Source
```bash
# Compile all Java files
javac -d build/classes src/clientserverchat/*.java

# Run with classpath
java -cp build/classes clientserverchat.ServerForm
java -cp build/classes clientserverchat.ClientForm
```

### IDE Setup
- NetBeans: Open as existing project (nbproject folder)
- Eclipse/IntelliJ: Import as Java project
- VS Code: Java Extension Pack recommended


### Common Issues

"Not connected to server"
- Ensure server is started first
- Check that port 1201 is not in use
- Verify firewall allows local connections

File transfer fails
- Check file permissions in Downloads folder
- Ensure file is not locked by another application
- Verify sufficient disk space

No sound notifications
- Check system audio settings
- Sound is non-critical - app works without it
- Audio failures are silently ignored

UI not responding
- Check Java version (17+ required)
- Ensure proper classpath
- Try restarting both applications

### Debug Mode
```bash
# Run with debugging enabled
java -agentlib:jdwp=transport=dt_socket,server=n,suspend=y,address=localhost:61114 -cp build/classes clientserverchat.ServerForm
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request
