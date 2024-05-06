
# WebSocket Server Setup

## Prerequisites

1. **Node.js**
   - Ensure you have Node.js version 16 installed to manage the WebSocket server. Follow these steps if you need to install it:
     1. Visit the [Node.js Download Page](https://nodejs.org/en/).
     2. Look for the "LTS" version labeled as "16.x.x".
     3. Click on the download link and follow the installation instructions provided on the website.

2. **wscat**
   - Install `wscat` for testing WebSocket connections using the following command:
     ```bash
     npm install -g wscat
     ```

## WebSocket Server Installation

Proceed to set up the WebSocket server:
```bash
npm install ws
```

## Starting the Server

Execute the following command to start your WebSocket server:
```bash
nohup node server.js &
```
The server will listen on port 8025 by default. You can change the port number by modifying the `server.js` file.

## Testing the Server

Connect to your WebSocket server using:
```bash
wscat -c ws://localhost:8025
```
This command initiates a WebSocket connection to your server, allowing you to send and receive messages for testing.