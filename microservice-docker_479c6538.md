## Building a Simple Dockerized Microservice

### Introduction

Docker is a containerization platform that allows developers to package and distribute applications along with their dependencies, ensuring consistent execution across different environments. This guide will provide a comprehensive walkthrough of building a simple microservice using Docker, suitable for beginners.

### Prerequisites

- Docker installed on your system
- A code editor or IDE
- A GitHub account

### Setting Up the Development Environment

1. Create a new directory for your project:

```
mkdir my-microservice
cd my-microservice
```

2. Initialize a new Git repository:

```
git init
```

### Creating the Project Structure

1. Create a `Dockerfile` in the project root directory. This file defines the steps to build the Docker image:

```
FROM python:3.8

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```

- `FROM python:3.8`: Specifies the base image for your container.
- `WORKDIR /app`: Sets the working directory within the container.
- `COPY requirements.txt .`: Copies the requirements file into the container.
- `RUN pip install -r requirements.txt`: Installs the Python dependencies.
- `COPY . .`: Copies the remaining project files into the container.
- `CMD ["python", "app.py"]`: Sets the command to run when the container starts.

2. Create a `requirements.txt` file:

```
Flask
```

This file specifies the Python dependencies for your application.

3. Create an `app.py` file:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello from my microservice!'

if __name__ == '__main__':
    app.run()
```

This is a simple Flask application that responds to HTTP GET requests on the root path.

### Running the Project

1. Build the Docker image:

```
docker build -t my-microservice .
```

2. Run the Docker container:

```
docker run -p 5000:5000 my-microservice
```

This command runs the container and exposes port 5000 within the container to port 5000 on your host machine.

3. Test the application:

Open a web browser and navigate to `http://localhost:5000`. You should see the message "Hello from my microservice!"

### Adding Code to Repository and Pushing to Remote

1. Add your code to the Git repository:

```
git add .
git commit -m "Initial commit"
```

2. Create a remote repository on GitHub:

Create a new repository on GitHub and copy the HTTPS URL.

3. Add the remote repository to your local repository:

```
git remote add origin <HTTPS URL>
```

4. Push your code to the remote repository:

```
git push origin main
```

Your microservice is now versioned and accessible on GitHub.