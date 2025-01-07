## Building a To-Do List Application Using Django

### Overview

In this guide, we will build a simple web application using Django for managing a to-do list. We will cover the following steps:

- Setting up the development environment
- Creating the project structure
- Writing the necessary code
- Running the project
- Testing the application
- Adding code to repository and pushing to remote

### Prerequisites

Before you begin, ensure you have the following installed:

- Python 3.6 or higher
- pip
- Django
- A text editor or IDE

### Step 1: Setting Up the Development Environment

1. Create a new virtual environment using `python -m venv venv`.
2. Activate the virtual environment using `source venv/bin/activate`.
3. Install Django using `pip install Django`.

### Step 2: Creating the Project Structure

1. Create a new directory for your project and navigate to it.
2. Create a new Django project using `django-admin startproject todo_app`.
3. Inside the `todo_app` directory, create an app for your to-do list using `python manage.py startapp todos`.

### Step 3: Writing the Necessary Code

**models.py** in `todos/models.py`:

```python
from django.db import models

class Todo(models.Model):
    title = models.CharField(max_length=200)
    description = models.TextField()
    completed = models.BooleanField(default=False)
```

**views.py** in `todos/views.py`:

```python
from django.shortcuts import render, redirect
from .models import Todo

def index(request):
    todos = Todo.objects.all()
    return render(request, 'todos/index.html', {'todos': todos})

def create(request):
    if request.method == 'POST':
        title = request.POST.get('title')
        description = request.POST.get('description')
        todo = Todo(title=title, description=description)
        todo.save()
        return redirect('index')
    return render(request, 'todos/create.html')

def update(request, id):
    todo = Todo.objects.get(id=id)
    if request.method == 'POST':
        todo.title = request.POST.get('title')
        todo.description = request.POST.get('description')
        todo.save()
        return redirect('index')
    return render(request, 'todos/update.html', {'todo': todo})

def delete(request, id):
    todo = Todo.objects.get(id=id)
    todo.delete()
    return redirect('index')
```

**urls.py** in `todos/urls.py`:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
    path('create/', views.create, name='create'),
    path('update/<int:id>/', views.update, name='update'),
    path('delete/<int:id>/', views.delete, name='delete'),
]
```

**index.html** in `todos/templates/todos/index.html`:

```html
{% extends 'base.html' %}

{% block content %}
<h1>To-Do List</h1>

<ul>
    {% for todo in todos %}
    <li>
        {{ todo.title }} - {{ todo.description }}
        <a href="{% url 'update' todo.id %}">Edit</a>
        <a href="{% url 'delete' todo.id %}">Delete</a>
    </li>
    {% endfor %}
</ul>

<a href="{% url 'create' %}">Add New To-Do</a>
{% endblock %}
```

**create.html** in `todos/templates/todos/create.html`:

```html
{% extends 'base.html' %}

{% block content %}
<h1>Add New To-Do</h1>

<form action="{% url 'create' %}" method="post">
    {% csrf_token %}
    <label for="title">Title:</label>
    <input type="text" name="title" id="title">
    <br>
    <label for="description">Description:</label>
    <textarea name="description" id="description"></textarea>
    <br>
    <input type="submit" value="Add To-Do">
</form>
{% endblock %}
```

**update.html** in `todos/templates/todos/update.html`:

```html
{% extends 'base.html' %}

{% block content %}
<h1>Edit To-Do</h1>

<form action="{% url 'update' todo.id %}" method="post">
    {% csrf_token %}
    <label for="title">Title:</label>
    <input type="text" name="title" id="title" value="{{ todo.title }}">
    <br>
    <label for="description">Description:</label>
    <textarea name="description" id="description">{{ todo.description }}</textarea>
    <br>
    <input type="submit" value="Update To-Do">
</form>
{% endblock %}
```

### Step 4: Running the Project

1. In the project directory, run `python manage.py runserver`.
2. Navigate to `http://127.0.0.1:8000/` in your browser.

### Step 5: Testing the Application

1. Create a new to-do item using the form on the home page.
2. Click on the "Edit" link for a to-do item and update its title and description.
3. Click on the "Delete" link to remove a to-do item.

### Step 6: Adding Code to Repository and Pushing to Remote

1. Create a new repository on GitHub or any other code hosting platform.
2. Initialize a new git repository in your project directory using `git init`.
3. Add all the code files to the staging area using `git add .`.
4. Commit the changes using `git commit -m "Initial commit"`.
5. Add the remote repository using `git remote add origin <remote_repository_url>`.
6. Push the code to the remote repository using `git push origin main`.

Congratulations! You have successfully built a simple web application using Django for managing a to-do list.