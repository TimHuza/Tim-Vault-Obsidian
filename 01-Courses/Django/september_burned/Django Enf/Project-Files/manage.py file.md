#django

If you are a beginner in Django, understanding `manage.py` is very important because you will use it **every day** while developing Django applications.

In simple words:

> **`manage.py` is a command-line tool that helps you interact with your Django project.**

It allows you to run your server, create database tables, create apps, make [[Migrations|migrations]], create users, and perform many other Django tasks.

---

## 1. Where does `manage.py` come from?

When you create a Django project:

```bash
django-admin startproject myproject
```

Django creates this structure:

```
myproject/
│
├── manage.py
│
└── myproject/
    │
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    ├── asgi.py
    └── wsgi.py
```

Notice:

```
myproject/
├── manage.py        <-- this file
│
└── myproject/
    ├── settings.py
    └── urls.py
```

`manage.py` is created automatically by Django.

---

# 2. What is `manage.py`?

`manage.py` is a **Python script**.

If you open it, you will see something like this:

```python
#!/usr/bin/env python
import os
import sys


def main():
    os.environ.setdefault(
        "DJANGO_SETTINGS_MODULE",
        "myproject.settings"
    )

    from django.core.management import execute_from_command_line

    execute_from_command_line(sys.argv)


if __name__ == "__main__":
    main()
```

It looks complicated, but let's break it down.

---

# 3. The main purpose of `manage.py`

The purpose of `manage.py` is:

```
Your command
      |
      v
 manage.py
      |
      v
 Django framework
      |
      v
 Perform the action
```

For example:

You type:

```bash
python manage.py runserver
```

The process:

```
You
 |
 |
 v
python manage.py runserver
 |
 |
 v
manage.py receives "runserver"
 |
 |
 v
Django understands:
"Start the development server"
 |
 |
 v
Server starts
```

---

# 4. What does `DJANGO_SETTINGS_MODULE` do?

This line is very important:

```python
os.environ.setdefault(
    "DJANGO_SETTINGS_MODULE",
    "myproject.settings"
)
```

It tells Django:

> "Use this settings file for this project."

Your project has:

```
myproject/
│
├── settings.py
```

Inside `settings.py` Django stores configuration:

```python
DATABASES = {
    ...
}

INSTALLED_APPS = [
    ...
]

MIDDLEWARE = [
    ...
]
```

Django needs to know:

- Which database should I use?
    
- Which apps exist?
    
- Where are templates?
    
- What is the secret key?
    
- What timezone is used?
    

`manage.py` connects Django to these settings.

---

# 5. What does `execute_from_command_line()` do?

This part:

```python
execute_from_command_line(sys.argv)
```

is the engine behind `manage.py`.

`sys.argv` contains your command.

Example:

You run:

```bash
python manage.py runserver
```

Python sees:

```python
sys.argv = [
    "manage.py",
    "runserver"
]
```

Then Django reads:

```
command = runserver
```

and executes the correct Django command.

---

# 6. Why do we need `manage.py`?

Without `manage.py`, you would have to manually configure Django every time.

For example, instead of:

```bash
python manage.py runserver
```

you would need something like:

```python
import os

os.environ["DJANGO_SETTINGS_MODULE"] = "myproject.settings"

from django.core.management import execute_from_command_line

execute_from_command_line(
    ["manage.py", "runserver"]
)
```

That would be annoying.

Django gives you `manage.py` as a shortcut.

---

# 7. Common commands using `manage.py`

You will use these a lot:

---

## Start Django development server

Command:

```bash
python manage.py runserver
```

Purpose:

Starts your local website.

Example:

```
Browser
   |
   v
localhost:8000
   |
   v
Django server
```

---

## Create a Django app

Command:

```bash
python manage.py startapp blog
```

Creates:

```
blog/
│
├── models.py
├── views.py
├── admin.py
├── apps.py
└── migrations/
```

---

## Create database migrations

Command:

```bash
python manage.py makemigrations
```

Meaning:

> "Django, look at my models and create instructions for database changes."

Example:

You create:

```python
class Product(models.Model):
    name = models.CharField(max_length=100)
```

Django creates a migration file.

---

## Apply migrations

Command:

```bash
python manage.py migrate
```

Meaning:

> "Execute those database changes."

Example:

Create the table:

```
Product table

id | name
---------
1  | Phone
2  | Laptop
```

---

## Create an admin user

Command:

```bash
python manage.py createsuperuser
```

Creates:

```
Username:
Email:
Password:
```

Then you can login at:

```
localhost:8000/admin/
```

---

## Open Django shell

Command:

```bash
python manage.py shell
```

Opens Python with Django loaded.

Example:

```python
>>> from blog.models import Post
>>> Post.objects.all()
```

---

# 8. Difference between `django-admin` and `manage.py`

This is a common beginner question.

## `django-admin`

Global Django command.

Used before you have a project.

Example:

```bash
django-admin startproject myproject
```

Meaning:

> "Django, create a new project."

---

## `manage.py`

Project-specific command.

Used after creating a project.

Example:

```bash
python manage.py runserver
```

Meaning:

> "Django, work with THIS project."

---

Think of it like this:

```
django-admin
      |
      |
      v
Creates Django projects


After project exists:

manage.py
      |
      |
      v
Controls that specific project
```

---

# 9. Why isn't `manage.py` inside the inner project folder?

You might wonder:

Why?

```
myproject/
│
├── manage.py        <-- here
│
└── myproject/
    ├── settings.py
```

Why not:

```
myproject/
│
└── myproject/
    ├── manage.py
    ├── settings.py
```

Because `manage.py` is meant to be the **entry point**.

Your workflow is:

```
Open terminal
      |
      v
Go to project folder
      |
      v
python manage.py command
```

It is like a remote control for your Django project.

---

# 10. Simple analogy

Imagine Django is a car.

```
Django project = Car

settings.py = Car configuration
              (engine settings, fuel, controls)

models.py = Car parts

views.py = Driver logic

manage.py = Car keys
```

Without the keys:

- the car exists
    
- the engine exists
    
- the parts exist
    

but you cannot easily start and control it.

`manage.py` is the key that lets you operate Django.

---

## Summary

|Thing|Purpose|
|---|---|
|`manage.py`|Command-line tool for your Django project|
|Created by|`django-admin startproject`|
|Written in|Python|
|Uses|Django management commands|
|Connects to|`settings.py`|
|Runs commands like|`runserver`, `migrate`, `createsuperuser`, `startapp`|
|Needed because|It simplifies controlling your Django project|

The easiest way to remember:

> **`django-admin` creates Django projects. `manage.py` manages Django projects.**