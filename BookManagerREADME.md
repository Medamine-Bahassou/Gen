## Building a Simple Book Management Application using Python Flask

### Overview

This guide will walk you through the process of building a simple web application using Python Flask for managing a book collection. We'll cover setting up the development environment, creating the project structure, writing the necessary code, running the project, testing the application, and pushing the code to a remote repository.

### Prerequisites

- Basic understanding of Python
- Familiarity with command line interface (CLI)
- Text editor or IDE

### Setting up the Development Environment

1. **Install Python:** Ensure you have Python 3.6 or later installed on your system. You can check by running `python --version` in the command line. If Python is not installed, visit the Python website to download the latest version.
2. **Create a Virtual Environment:** Virtual environments help isolate project dependencies. Create a virtual environment using `python -m venv venv`. Activate the environment using `source venv/bin/activate` on Linux/macOS or `venv\Scripts\activate` on Windows.
3. **Install Flask:** Install Flask using `pip install Flask`.

### Creating the Project Structure

1. **Create a New Directory:** Create a new directory for your project, e.g., `book-manager`.
2. **Initialize Git Repository:** Initialize a Git repository within the project directory using `git init`.
3. **Create Project Files:** Create the following files within the project directory:

   - `app.py`: Main application file
   - `requirements.txt`: File listing project dependencies
   - `README.md`: Documentation file

### Writing the Code

**app.py**

```python
from flask import Flask, render_template, request, redirect, url_for

app = Flask(__name__)

books = []

@app.route('/')
def index():
    return render_template('index.html', books=books)

@app.route('/add', methods=['GET', 'POST'])
def add():
    if request.method == 'POST':
        book = request.form.get('book')
        books.append(book)
        return redirect(url_for('index'))
    return render_template('add.html')

if __name__ == '__main__':
    app.run(debug=True)
```

**index.html**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Book Manager</title>
</head>
<body>
  <h1>Book Manager</h1>
  <ul>
    {% for book in books %}
      <li>{{ book }}</li>
    {% endfor %}
  </ul>
  <a href="{{ url_for('add') }}">Add a Book</a>
</body>
</html>
```

**add.html**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Add a Book</title>
</head>
<body>
  <h1>Add a Book</h1>
  <form action="{{ url_for('add') }}" method="POST">
    <label for="book">Book:</label>
    <input type="text" name="book" id="book">
    <input type="submit" value="Add">
  </form>
</body>
</html>
```

### Running the Project

1. **Start the Application:** Run the application using `flask run` from the project directory.
2. **Open the Browser:** Open a web browser and navigate to `http://127.0.0.1:5000/`.

### Testing the Application

1. **Add a Book:** Click on the "Add a Book" link and enter a book title. Click "Add."
2. **Verify Book Added:** The book should appear in the list on the homepage.

### Adding Code to Repository and Pushing to Remote

1. **Add Code to Staging:** Stage the changes using `git add .`.
2. **Commit Changes:** Commit the changes with a message using `git commit -m "Added book management functionality"`.
3. **Create Remote Repository:** Create a remote repository on GitHub or other Git hosting service.
4. **Push to Remote:** Push the changes to the remote repository using `git push -u origin main`.

### Conclusion

Congratulations! You have successfully built a simple web application using Python Flask for managing a book collection. This guide provides a solid foundation for further exploration and development of Flask applications.