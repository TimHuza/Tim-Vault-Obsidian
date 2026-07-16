#django 


```python
if settings.DEBUG:
    urlpatterns += static(
        settings.MEDIA_URL,
        document_root=settings.MEDIA_ROOT
    )
```

The purpose of this code is:

> **Tell Django how to serve uploaded files (images, videos, documents) during development.**

Let's go piece by piece.

---

# 1. `if settings.DEBUG:`

```python
if settings.DEBUG:
```

This is a Python `if` statement.

It asks:

> "Is Django running in debug mode?"

In `settings.py` you usually have:

```python
DEBUG = True
```

during development.

So this:

```python
if settings.DEBUG:
```

becomes:

```python
if True:
```

and Django runs the code below it.

---

Why only when `DEBUG=True`?

Because Django's built-in file serving is **only for development**.

When your website goes to production:

```python
DEBUG = False
```

you normally use:

- Nginx
    
- Apache
    
- AWS S3
    
- Cloud storage
    

to serve media files.

---

# 2. `urlpatterns`

You probably have something like:

```python
urlpatterns = [
    path("admin/", admin.site.urls),
]
```

This is a list of URL rules.

It tells Django:

```
URL requested        →  What should happen?

/admin/              →  Open Django admin
/products/           →  Show products page
/login/              →  Login page
```

Example:

```python
urlpatterns = [
    path("admin/", admin.site.urls),
]
```

means:

When someone visits:

```
localhost:8000/admin/
```

Django knows what to do.

---

# 3. `+=`

```python
urlpatterns += something
```

means:

> "Add more items to this list."

Example:

Before:

```python
urlpatterns = [
    path("admin/", admin.site.urls),
]
```

After:

```python
urlpatterns += [
    path("media/", ...)
]
```

Now:

```python
urlpatterns = [
    path("admin/", admin.site.urls),
    path("media/", ...)
]
```

We are adding a new URL route.

---

# 4. `static()`

```python
static(
    settings.MEDIA_URL,
    document_root=settings.MEDIA_ROOT
)
```

This function creates a URL pattern for serving files.

It comes from:

```python
from django.conf.urls.static import static
```

---

It connects these two things:

```python
MEDIA_URL
```

and

```python
MEDIA_ROOT
```

Remember:

```python
MEDIA_URL = "/media/"
```

means:

> "The browser uses this URL."

and:

```python
MEDIA_ROOT = BASE_DIR / "media"
```

means:

> "The files are stored here."

---

So:

```python
static(
    "/media/",
    document_root="myproject/media/"
)
```

means:

> "If someone requests `/media/`, look inside the `myproject/media/` folder."

---

# 5. `document_root=settings.MEDIA_ROOT`

This part:

```python
document_root=settings.MEDIA_ROOT
```

tells Django:

> "This is the actual folder where the files exist."

Example:

Your project:

```
mywebsite/
│
├── media/
│   └── cat.jpg
│
├── manage.py
└── settings.py
```

Your settings:

```python
MEDIA_ROOT = BASE_DIR / "media"
MEDIA_URL = "/media/"
```

Now Django creates a connection:

```
Browser URL                  Computer folder

/media/cat.jpg   ───────►    mywebsite/media/cat.jpg
```

---

# Full example

Imagine you upload:

```
dog.png
```

Django saves it:

```
media/dog.png
```

Your browser requests:

```
http://localhost:8000/media/dog.png
```

Django checks:

```python
urlpatterns
```

It finds:

```python
static(
    "/media/",
    document_root="media/"
)
```

Django thinks:

"Someone requested `/media/dog.png`."

"Remove `/media/`."

"Look for:

```
media/dog.png
```

"

It finds the file and sends it back.

---

# Visual flow

```
Browser
   |
   |  GET /media/cat.jpg
   |
   ↓

urls.py

if DEBUG:
    static(
        "/media/",
        media/
    )

   |
   ↓

MEDIA_ROOT

myproject/
    media/
        cat.jpg

   |
   ↓

Return image
```

---

# In one sentence:

```python
urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

means:

> "During development, add a URL route so that anything starting with `/media/` is loaded from the folder defined by `MEDIA_ROOT`."

This line is basically the **bridge between the browser URL and the actual folder on your computer**.