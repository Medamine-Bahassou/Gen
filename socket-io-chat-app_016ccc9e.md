## Building a Simple Chat App with Socket.io

### Project Overview

We'll build a simple chat application that allows users to send and receive messages in real-time. We'll use Socket.io for real-time communication.

### Setting Up the Development Environment

1. Install Node.js and npm.
2. Create a new directory for your project and navigate to it.
3. Initialize a new npm project by running `npm init -y`.

### Creating the Project Structure

Create the following files:

- `app.js`: This will be the main server file.
- `public/index.html`: This will be the client-side HTML file.
- `public/app.js`: This will be the client-side JavaScript file.

### Writing the Code

**app.js**

```javascript
const express = require('express');
const socketIO = require('socket.io');

const app = express();
const server = app.listen(3000, () => console.log('Server is running on port 3000'));
const io = socketIO(server);

io.on('connection', (socket) => {
  console.log('New user connected');

  socket.on('chat message', (msg) => {
    io.emit('chat message', msg);
  });

  socket.on('disconnect', () => {
    console.log('User disconnected');
  });
});
```

**public/index.html**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Chat App</title>
</head>
<body>
  <input type="text" id="message" placeholder="Enter message">
  <button id="send-button">Send</button>

  <ul id="messages"></ul>

  <script src="/socket.io/socket.io.js"></script>
  <script src="app.js"></script>
</body>
</html>
```

**public/app.js**

```javascript
const socket = io();

const messageInput = document.getElementById('message');
const sendButton = document.getElementById('send-button');
const messagesList = document.getElementById('messages');

sendButton.addEventListener('click', () => {
  const msg = messageInput.value;
  socket.emit('chat message', msg);
  messageInput.value = '';
});

socket.on('chat message', (msg) => {
  const li = document.createElement('li');
  li.textContent = msg;
  messagesList.appendChild(li);
});
```

### Running the Project

1. Install Socket.io client library in your project: `npm install socket.io-client`.
2. Start the server by running `node app.js`.
3. Open `public/index.html` in a browser.

### Testing the Application

1. Type a message in the input field and click the "Send" button.
2. You should see the message appear in the chat window.
3. Open another browser tab and navigate to the same URL.
4. Type a message in the second tab and click "Send".
5. You should see the message appear in both tabs.

### Adding Code to Repository and Pushing to Remote

1. Create a new repository on GitHub or any other code hosting platform.
2. Add all your project files to the repository.
3. Commit your changes and push them to the remote repository.
4. Share the repository URL with others to collaborate on the project.