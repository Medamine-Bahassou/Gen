## Building a Simple Microservice Application with Docker

### Introduction

Docker is a platform that allows developers to build, ship, and run applications in containers. Containers are isolated environments that contain everything an application needs to run, including the code, runtime, libraries, and system tools. This makes it easy to deploy and manage applications on any infrastructure, from on-premises servers to cloud platforms.

In this guide, we will create a simple microservice application using Docker. A microservice is a small, independent service that performs a specific task. We will use the Express.js framework to build our microservice and Docker to containerize it.

### Prerequisites

Before you begin, make sure you have the following installed on your system:

- Docker Desktop: https://www.docker.com/products/docker-desktop
- Node.js: https://nodejs.org/en/

### Setting Up the Development Environment

1. Open a terminal window.
2. Create a new directory for your project:

```
mkdir docker-microservice
cd docker-microservice
```

3. Initialize a new Node.js project:

```
npm init -y
```

### Creating the Project Structure

1. Create a new directory for the source code:

```
mkdir src
```

2. Inside the `src` directory, create a new file named `app.js`:

```
touch src/app.js
```

### Writing the Code

1. Open `src/app.js` in your preferred code editor.
2. Add the following code to the file:

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, world!');
});

app.listen(3000, () => {
  console.log('Server is listening on port 3000');
});
```

This code creates a simple Express.js application that responds to HTTP GET requests with the message "Hello, world!".

### Creating the Dockerfile

1. Create a new file named `Dockerfile` in the root of your project directory.
2. Add the following content to the file:

```
FROM node:16

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

CMD ["node", "src/app.js"]
```

This Dockerfile specifies the following instructions:

- `FROM node:16`: This line specifies that we are using the official Node.js image with version 16 as the base image for our container.
- `WORKDIR /usr/src/app`: This line sets the working directory inside the container to `/usr/src/app`.
- `COPY package*.json ./`: This line copies the `package.json` file from the host machine to the container.
- `RUN npm install`: This line runs the `npm install` command to install the dependencies for our application.
- `COPY . .`: This line copies the rest of the files from the host machine to the container.
- `CMD ["node", "src/app.js"]`: This line specifies the command that will be executed when the container starts.

### Building the Docker Image

1. Open a terminal window.
2. Navigate to the root of your project directory.
3. Run the following command to build the Docker image:

```
docker build -t docker-microservice .
```

This command will build a Docker image and tag it with the name `docker-microservice`.

### Running the Docker Container

1. Run the following command to run the Docker container:

```
docker run -p 3000:3000 docker-microservice
```

This command will run the Docker container and expose port 3000 inside the container to port 3000 on the host machine.

### Testing the Application

1. Open a web browser and navigate to `http://localhost:3000`.
2. You should see the message "Hello, world!" in the browser window.

### Adding Code to Repository and Pushing to Remote

1. Add the changes to your local Git repository:

```
git add .
```

2. Commit the changes:

```
git commit -m "feat: add Docker support"
```

3. Push the changes to a remote repository, such as GitHub:

```
git push origin main
```

### Conclusion

In this guide, we created a simple microservice application using Docker. We learned how to set up the development environment, create the project structure, write the code, build the Docker image, and run the Docker container. We also tested the application and added the code to a remote repository.