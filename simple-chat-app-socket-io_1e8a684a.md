## Building a Simple Chat App with Socket.io

### Prerequisites

- Node.js installed
- Basic understanding of JavaScript and HTML

### Creating a Repository

1. Open your preferred Git client (e.g., GitHub Desktop, GitKraken)
2. Create a new repository
3. Give it a name like "simple-chat-socket.io"
4. Clone the repository to your local machine

### Setting Up the Development Environment

1. Open a terminal window
2. Change directory to the cloned repository
3. Run `npm init` to initialize a new Node.js project
4. Install Socket.io using `npm install socket.io`

### Creating the Project Structure

1. Create a directory called `client` for the client-side code
2. Create a file called `index.html` inside the `client` directory
3. Create a directory called `server` for the server-side code
4. Create a file called `index.js` inside the `server` directory

### Writing the Code

**Client-Side Code (`client/index.html`):**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Simple Chat App</title>
</head>
<body>
  <h1>Chat App</h1>
  <input type="text" id="message-input" placeholder="Enter message">
  <button id="send-button">Send</button>
  <ul id="messages"></ul>

  <script src="/socket.io/socket.io.js"></script>
  <script>
    const socket = io();

    const messageInput = document.getElementById('message-input');
    const sendButton = document.getElementById('send-button');
    const messages = document.getElementById('messages');

    sendButton.addEventListener('click', () => {
      const message = messageInput.value;
      socket.emit('message', message);
      messageInput.value = '';
    });

    socket.on('message', (message) => {
      const li = document.createElement('li');
      li.textContent = message;
      messages.appendChild(li);
    });
  </script>
</body>
</html>
```

**Server-Side Code (`server/index.js`):**

```javascript
const express = require('express');
const socketIO = require('socket.io');

const app = express();
app.use(express.static('client'));

const server = app.listen(3000, () => {
  console.log('Server listening on port 3000');
});

const io = socketIO(server);

io.on('connection', (socket) => {
  console.log('New client connected');

  socket.on('message', (message) => {
    console.log(`Message received: ${message}`);
    io.emit('message', message);
  });

  socket.on('disconnect', () => {
    console.log('Client disconnected');
  });
});
```

### Running the Project

1. In the terminal window, change directory to the project root
2. Run `npm start`
3. Open your browser and navigate to `http://localhost:3000`

### Testing the Application

1. In the browser, enter a message in the input field and click the "Send" button
2. Verify that the message appears in the chat window

### Adding Code to Repository and Pushing to Remote

1. Stage the changes using `git add .`
2. Commit the changes using `git commit -m "Added chat app functionality"`
3. Push the changes to the remote repository using `git push origin master`