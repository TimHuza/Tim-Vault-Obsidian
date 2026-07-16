#django

When you create a Django project using [[Start project command]]:

```bash
django-admin startproject myproject
```

Django creates a **project package**:

```
myproject/
│
├── manage.py
│
└── myproject/
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    ├── asgi.py
    └── wsgi.py
```

The second `myproject` folder is **not your app**. It is your **Django project configuration package**.

There is also **[[manage.py file]] file created within the `myproject` folder.

A common beginner confusion:
- **Project** = the entire Django website/application configuration
- **App** = a feature/module inside your project (blog, users, products, etc.)

Example:

```
mywebsite/              ← Django project
│
├── manage.py
│
├── mywebsite/          ← project configuration
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
└── blog/               ← Django app
    ├── models.py
    ├── views.py
    ├── urls.py
    └── templates/
```

Now let's explain each file.

---

# 1. `__init__.py`

## What is this file?

`__init__.py` tells Python:

> "This folder is a Python package."

A package is simply a folder containing Python code that Python can import.

Example:

```
myproject/
│
├── __init__.py
├── settings.py
└── urls.py
```

Because `__init__.py` exists, Python understands:

```
myproject
```

is something it can import.

---

## What does it do?

Usually:

**Nothing.**

It is often empty:

```python
# __init__.py
```

But it allows imports like:

```python
from myproject import settings
```

Python knows:

```
myproject/
    settings.py
```

is part of the package.

---

## Why do we need it?

Without it, older versions of Python would not recognize the folder as a package.

Django uses many imports internally, so this file helps organize the project.

---

## Purpose

Think of it as:

> "The sign on the door saying: this folder contains Python code."

---

# 2. `settings.py`

This is probably the **most important file**.

---

## What is this file?

`settings.py` contains all the configuration of your Django project.

It controls:

- database settings
    
- installed applications
    
- security settings
    
- templates
    
- static files
    
- middleware
    
- language
    
- timezone
    
- debug mode
    

---

Example:

```python
DEBUG = True
```

Means:

During development, show detailed error pages.

---

Example:

```python
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "blog",
]
```

This tells Django:

> "These apps exist in my project."

---

Example:

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.sqlite3",
        "NAME": "db.sqlite3",
    }
}
```

This tells Django:

> "Use SQLite as my database."

---

## What does it do?

When Django starts, it loads:

```
settings.py
```

and reads:

- what apps exist
    
- what database to use
    
- where templates are
    
- security configuration
    
- installed plugins
    

---

## Why do we need it?

Without settings Django would not know:

- where your database is
    
- what apps belong to the project
    
- how to handle requests
    
- what features are enabled
    

---

## Purpose

Think of it as:

> "The control panel of your Django website."

---

# 3. `urls.py`

## What is this file?

`urls.py` controls **URL routing**.

It answers:

> "When a user visits this URL, which code should run?"

---

Example:

User visits:

```
https://example.com/about/
```

Django checks:

```python
urlpatterns = [
    path("about/", views.about)
]
```

Then Django says:

"Okay, `/about/` should call the `about()` function."

---

Example:

```python
from django.urls import path
from . import views


urlpatterns = [
    path("", views.home),
    path("about/", views.about),
]
```

Meaning:

|URL|Function|
|---|---|
|`/`|home()|
|`/about/`|about()|

---

## What does it do?

It creates the connection:

```
URL
 |
 v
View
 |
 v
HTML response
```

Example:

```
Browser
   |
   |
/products/
   |
   |
urls.py
   |
   |
products.views.list_products()
   |
   |
HTML page
```

---

## Why do we need it?

Without `urls.py` Django would not know:

- which page to show
    
- which function handles a request
    
- where users should go

---

## Purpose

Think of it as:

> "The traffic controller of your website."

It directs users to the correct place.

---

# 4. `wsgi.py`

## What is this file?

WSGI means:

**Web Server Gateway Interface**

It is a bridge between:

```
Web Server
      |
      |
      v
Django Application
```

---

Example:

A user visits:

```
www.mywebsite.com
```

The request goes:

```
Browser
   |
   |
Nginx / Apache
   |
   |
wsgi.py
   |
   |
Django
```

---

## What does it contain?

Usually:

```python
import os

from django.core.wsgi import get_wsgi_application


os.environ.setdefault(
    "DJANGO_SETTINGS_MODULE",
    "myproject.settings"
)

application = get_wsgi_application()
```

This creates the Django application that the server runs.

---

## Why do we need it?

When you deploy Django:

Example:

- AWS
    
- DigitalOcean
    
- Render
    
- Heroku

The server needs a way to start your Django application.

It looks for:

```
wsgi.py
```

---

## Purpose

Think of it as:

> "The entrance door for traditional web servers."

---

# 5. `asgi.py`

## What is this file?

ASGI means:

**Asynchronous Server Gateway Interface**

It is the newer version of WSGI.

It supports:
- normal HTTP requests
    
- [[WebSockets]]
    
- asynchronous programming

---

Example:

Normal website:

```
User
 |
HTTP request
 |
Django
```

ASGI allows:

```
User
 |
WebSocket connection
 |
Django
 |
Real-time updates
```

---

Examples where ASGI is useful:

- chat applications
    
- multiplayer games
    
- notifications
    
- live dashboards
    

---

## What does it contain?

Similar to WSGI:

```python
import os

from django.core.asgi import get_asgi_application


os.environ.setdefault(
    "DJANGO_SETTINGS_MODULE",
    "myproject.settings"
)

application = get_asgi_application()
```

---

## Why do we need it?

Modern applications often need real-time features.

For example:

A messaging app:

```
User A sends message

        ↓

Django immediately pushes it

        ↓

User B receives it
```

ASGI helps Django handle this.

---

## Purpose

Think of it as:

> "The entrance door for modern asynchronous servers."

---

# WSGI vs ASGI

||WSGI|ASGI|
|---|---|---|
|Full name|Web Server Gateway Interface|Asynchronous Server Gateway Interface|
|Age|Older|Newer|
|Handles|HTTP|HTTP + WebSockets|
|Async support|No|Yes|
|Used for|Traditional websites|Modern real-time apps|

---

# How all files work together

Imagine someone visits your website:

```
User opens:

example.com/products/
```

### Step 1

Server receives request:

```
Browser
   |
   v
WSGI/ASGI
```

---

### Step 2

Django starts:

```
settings.py
```

loads configuration.

---

### Step 3

Django checks:

```
urls.py
```

It asks:

"Who handles `/products/`?"

---

### Step 4

URL calls:

```
views.py
```

Example:

```python
def products(request):
    return render(request, "products.html")
```

---

### Step 5

Response goes back:

```
Django
 |
 v
Browser
```

---

# Simple analogy

Imagine Django is a restaurant:

|Django file|Restaurant role|
|---|---|
|`settings.py`|Restaurant rules and configuration|
|`urls.py`|Receptionist directing customers|
|`views.py`|Chef preparing the order|
|`models.py`|Storage/inventory system|
|`wsgi.py`|Front door for normal customers|
|`asgi.py`|Front door for customers needing live service|
|`__init__.py`|Sign saying "this is a restaurant"|

---

## Beginner summary

|File|Main purpose|
|---|---|
|`__init__.py`|Makes folder a Python package|
|`settings.py`|Controls Django configuration|
|`urls.py`|Maps URLs to views|
|`wsgi.py`|Allows servers to run Django (traditional)|
|`asgi.py`|Allows servers to run Django asynchronously|

If you are learning Django, the files you will work with **most often** are:

1. `settings.py` ⭐⭐⭐
    
2. `urls.py` ⭐⭐⭐
    
3. `views.py` ⭐⭐⭐
    
4. `models.py` ⭐⭐⭐
    

`wsgi.py` and `asgi.py` are mostly important when you deploy your project.