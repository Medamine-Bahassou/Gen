## Building a Simple To-Do Management App with Django

### Introduction

In this guide, we'll build a basic web application using Django, a popular Python web framework, to manage a to-do list. We'll cover everything from setting up the development environment to testing and deploying the application.

### Prerequisites

- Python 3.7 or later
- pipenv
- Git

### Step 1: Create a Repository

Create a new repository on GitHub or GitLab.

### Step 2: Setting Up the Development Environment

**Install pipenv**

```bash
pip install pipenv
```

**Create a virtual environment**

```bash
pipenv install django
```

### Step 3: Creating the Project Structure

**Create a new Django project**

```bash
django-admin startproject todo
```

**Create the to-do app**

```bash
python manage.py startapp todo
```

**Configure the settings.py file**

```python
# settings.py

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'todo.apps.TodoConfig',  # Add the todo app
]
```

### Step 4: Writing the Necessary Code

**Create the models.py file**

```python
# models.py

from django.db import models

class Todo(models.Model):
    title = models.CharField(max_length=255)
    description = models.TextField()
    completed = models.BooleanField(default=False)
```

**Create the views.py file**

```python
# views.py

from django.shortcuts import render, redirect
from .models import Todo

def index(request):
    todos = Todo.objects.all()
    context = {
        'todos': todos
    }
    return render(request, 'todo/index.html', context)

def create(request):
    if request.method == 'POST':
        title = request.POST['title']
        description = request.POST['description']
        Todo.objects.create(title=title, description=description)
        return redirect('index')
    else:
        return render(request, 'todo/create.html')

def update(request, id):
    todo = Todo.objects.get(id=id)
    if request.method == 'POST':
        todo.title = request.POST['title']
        todo.description = request.POST['description']
        todo.save()
        return redirect('index')
    else:
        context = {
            'todo': todo
        }
        return render(request, 'todo/update.html', context)

def delete(request, id):
    todo = Todo.objects.get(id=id)
    todo.delete()
    return redirect('index')
```

**Create the templates**

```html
# index.html

{% extends 'base.html' %}

{% block content %}
<h1>To-Do List</h1>
<ul>
    {% for todo in todos %}
    <li>
        {{ todo.title }} - {{ todo.description }} - {{ todo.completed }}
        <a href="{% url 'update' todo.id %}">Update</a>
        <a href="{% url 'delete' todo.id %}">Delete</a>
    </li>
    {% endfor %}
</ul>
<a href="{% url 'create' %}">Create New To-Do</a>
{% endblock %}

# create.html

{% extends 'base.html' %}

{% block content %}
<h1>Create New To-Do</h1>
<form method="POST">
    {% csrf_token %}
    <label for="title">Title:</label>
    <input type="text" name="title" id="title">
    <br>
    <label for="description">Description:</label>
    <textarea name="description" id="description"></textarea>
    <br>
    <input type="submit" value="Create">
</form>
{% endblock %}

# update.html

{% extends 'base.html' %}

{% block content %}
<h1>Update To-Do</h1>
<form method="POST">
    {% csrf_token %}
    <label for="title">Title:</label>
    <input type="text" name="title" id="title" value="{{ todo.title }}">
    <br>
    <label for="description">Description:</label>
    <textarea name="description" id="description">{{ todo.description }}</textarea>
    <br>
    <input type="submit" value="Update">
</form>
{% endblock %}
```

### Step 5: Running the Project

**Run the development server**

```bash
python manage.py runserver
```

### Step 6: Testing the Application

**Create a superuser**

```bash
python manage.py createsuperuser
```

**Login to the admin interface**

```
http://127.0.0.1:8000/admin/
```

**Create, update, and delete to-dos**

### Step 7: Adding Code to Repository and Pushing to Remote

**Add the code to the repository**

```bash
git add .
```

**Commit the changes**

```bash
git commit -m "Initial commit"
```

**Push the changes to the remote repository**

```bash
git push origin main
```

### Conclusion

You've now successfully built a simple web application using Django for managing a to-do list. You can further customize and extend the application to meet your specific requirements.