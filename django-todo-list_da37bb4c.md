## Building a Simple To-Do List Application with Django

### Introduction

In this guide, we'll create a simple web application using Django for managing a to-do list. We'll cover everything from setting up the development environment to writing the necessary code and testing the application.

### Prerequisites

- Python 3.6 or later
- pip
- virtualenv

### Setting Up the Development Environment

1. Create a virtual environment:

   ```
   python3 -m venv venv
   source venv/bin/activate
   ```

2. Install Django:

   ```
   pip install django
   ```

### Creating the Project Structure

1. Create a new Django project:

   ```
   django-admin startproject myproject
   ```

2. Navigate into the project directory:

   ```
   cd myproject
   ```

3. Create a new Django app for the to-do list:

   ```
   python manage.py startapp todos
   ```

### Writing the Necessary Code

1. In the `todos` app, create a model for the to-do items:

   ```python
   # models.py
   from django.db import models

   class ToDo(models.Model):
       title = models.CharField(max_length=100)
       description = models.TextField()
       created_at = models.DateTimeField(auto_now_add=True)
       updated_at = models.DateTimeField(auto_now=True)
   ```

2. In the `todos` app, create a views for the to-do list:

   ```python
   # views.py
   from django.shortcuts import render, redirect
   from .models import ToDo

   def index(request):
       todos = ToDo.objects.all()
       return render(request, 'todos/index.html', {'todos': todos})

   def create(request):
       if request.method == 'POST':
           title = request.POST.get('title')
           description = request.POST.get('description')
           ToDo.objects.create(title=title, description=description)
           return redirect('todos:index')
       return render(request, 'todos/create.html')

   def update(request, pk):
       todo = ToDo.objects.get(pk=pk)
       if request.method == 'POST':
           title = request.POST.get('title')
           description = request.POST.get('description')
           todo.title = title
           todo.description = description
           todo.save()
           return redirect('todos:index')
       return render(request, 'todos/update.html', {'todo': todo})

   def delete(request, pk):
       todo = ToDo.objects.get(pk=pk)
       todo.delete()
       return redirect('todos:index')
   ```

3. In the `myproject` project, create a `urls.py` file for the to-do app:

   ```python
   # urls.py
   from django.urls import path
   from .todos import views

   urlpatterns = [
       path('todos/', views.index, name='todos:index'),
       path('todos/create/', views.create, name='todos:create'),
       path('todos/<int:pk>/update/', views.update, name='todos:update'),
       path('todos/<int:pk>/delete/', views.delete, name='todos:delete'),
   ]
   ```

4. In the `myproject` project, create a `settings.py` file and add the following line:

   ```python
   INSTALLED_APPS = [
       'django.contrib.admin',
       'django.contrib.auth',
       'django.contrib.contenttypes',
       'django.contrib.sessions',
       'django.contrib.messages',
       'django.contrib.staticfiles',
       'todos',  # Add the 'todos' app
   ]
   ```

### Running the Project

1. Migrate the database:

   ```
   python manage.py migrate
   ```

2. Run the development server:

   ```
   python manage.py runserver
   ```

3. Open your browser and go to `http://127.0.0.1:8000/todos/`

### Testing the Application

1. Create a test case for the `ToDo` model:

   ```python
   # tests.py
   from django.test import TestCase
   from .models import ToDo

   class ToDoModelTest(TestCase):

       def test_create_todo(self):
           todo = ToDo.objects.create(title='Test To-Do', description='This is a test to-do')
           self.assertEqual(todo.title, 'Test To-Do')
           self.assertEqual(todo.description, 'This is a test to-do')
   ```

2. Run the tests:

   ```
   python manage.py test
   ```

### Adding Code to Repository and Pushing to Remote

1. Create a new Git repository for the project:

   ```
   git init
   ```

2. Add the project files to the staging area:

   ```
   git add .
   ```

3. Commit the changes to the local repository:

   ```
   git commit -m "Initial commit"
   ```

4. Create a remote repository on GitHub or any other code hosting platform.

5. Add the remote repository as a remote:

   ```
   git remote add origin <remote_repository_url>
   ```

6. Push the changes to the remote repository:

   ```
   git push origin main
   ```

### Conclusion

In this guide, we created a simple web application using Django for managing a to-do list. We covered everything from setting up the development environment to writing the necessary code and testing the application. We also showed you how to add the code to a Git repository and push it to a remote.