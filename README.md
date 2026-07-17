# WebRTC Video Conferencing App

A minimal real-time video conferencing application built using WebRTC, React.js and Socket.IO.

This project enables two peers to establish a direct peer-to-peer audio/video connection through WebRTC, with Socket.IO used for signaling between clients.

The project was developed as a college mini project and includes optimizations using **Trickle ICE** to significantly reduce connection setup time. Cross-platform connectivity was also tested successfully across different devices and networks using Ngrok.

[Watch Demo on YouTube](https://youtu.be/dtX3JcCir84)

## Features

- Real-time peer-to-peer video/audio communication
- WebRTC-based connection handling
- Socket.IO signaling server
- Faster connection setup using Trickle ICE
- Cross-device and cross-network working verified using Ngrok
- Ability to reconnect without refreshing the page

## Tech Stack

### Frontend
- React.js

### Backend
- Express.js
- Socket.IO

### Real-Time Communication
- WebRTC
- Trickle ICE

### Testing / Tunneling
- Ngrok

## How It Works

1. Two clients open the application.
2. Socket.IO is used to exchange signaling data between peers.
3. WebRTC establishes a direct peer-to-peer connection.
4. Audio and video streams are exchanged directly between clients.

The signaling server is only responsible for connection negotiation and is not involved in media streaming after the connection is established.

## Setup Instructions
### Prerequisites
* Node.js
* Ngrok (free)
* HTTPS enabled for localhost (required for camera/microphone access) - such as through `mkcert`

### Installation
#### 1. Clone the Repository
`git clone <repo-url>`

#### 2. Switch to the Latest Branch
`git checkout trickle`

#### 3. Install Dependencies
Run the following inside every directory containing a package.json file:
`npm install`

### Environment Variables
1. Root Directory
*  Create a `.env` file in the project root:
  `REACT_APP_SERVER_URL=<your-ngrok-server-url>`
*  Example local server URL:
`http://localhost:5000`

2. `signaling_server` directory:
*  Create another `.env` file inside `signaling_server`:
`REACT_APP_NGROK_URL=<your-ngrok-client-url>`
*  Example local client URL:
`https://localhost:3000`

## Running the Application
### 1. Start Ngrok Tunnels
Expose both:
* React client
* Signaling server

### 2. Start the Signaling Server
Inside `signaling_server`: `nodemon server.js`

### 3. Start the React Client
`npm start`

## Using the Application
1. Open the client in two browser tabs or on two separate devices.
2. On one client, click: `Open Connection`
3. On the second client, click: `Answer Connection`
4. The peers should connect and begin exchanging audio/video streams.
5. Either client can terminate the session using: `Close Connection`
6. The connection can be re-established without refreshing the page.
