#django 


```Python
MEDIA_URL = '/media/'

MEDIA_ROOT = BASE_DIR / 'media'
```

## 1. `MEDIA_ROOT`

```python
MEDIA_ROOT = BASE_DIR / 'media'
```

### Meaning:

`MEDIA_ROOT` tells Django:

> "Save uploaded files inside this folder."

Let's break it down.

### `BASE_DIR`

`BASE_DIR` is usually defined near the top of `settings.py`:

```python
BASE_DIR = Path(__file__).resolve().parent.parent
```

It represents the **main folder of your Django project**.

Example project:

```
mywebsite/
│
├── manage.py
├── mywebsite/
│   ├── settings.py
│   └── urls.py
│
└── shop/
    ├── models.py
```

Here:

```
BASE_DIR = mywebsite/
```

---

Now:

```python
MEDIA_ROOT = BASE_DIR / 'media'
```

means:

```
mywebsite/media/
```

Django will create/use this folder:

```
mywebsite/
│
├── media/
│   ├── profile.jpg
│   ├── product1.png
│   └── documents.pdf
│
├── manage.py
└── settings.py
```

So:

**MEDIA_ROOT = physical location on your computer**

---

## 2. `MEDIA_URL`

```python
MEDIA_URL = '/media/'
```

This tells Django:

> "When someone requests a media file, use this URL prefix."

For example:

Your file:

```
media/profile.jpg
```

is stored here:

```
mywebsite/media/profile.jpg
```

But users don't access it with:

```
C:\Users\Tim\projects\mywebsite\media\profile.jpg
```

Instead, they use a URL:

```
http://localhost:8000/media/profile.jpg
```

The `/media/` part comes from:

```python
MEDIA_URL = '/media/'
```

---

## How they work together

Imagine a user uploads:

```
cat.jpg
```

Your model:

```python
class Product(models.Model):
    image = models.ImageField(upload_to='products/')
```

Django saves it:

```
MEDIA_ROOT
    |
    ↓
mywebsite/media/products/cat.jpg
```

So physically:

```
mywebsite/
│
├── media/
│   └── products/
│       └── cat.jpg
```

But the browser sees:

```
MEDIA_URL
    |
    ↓
http://localhost:8000/media/products/cat.jpg
```

---

## Simple analogy

Imagine your computer is a library.

### `MEDIA_ROOT`

is the **storage room**:

```
Storage Room:
media/
    books/
    pictures/
    videos/
```

It tells Django:

> "Put uploaded files here."

---

### `MEDIA_URL`

is the **public entrance sign**:

```
Website:
http://library.com/media/
```

It tells Django:

> "People can access files through this URL."

---

## Why do we need both?

Because they solve different problems.

### `MEDIA_ROOT`

works with the server:

```
Where is the file saved?
```

Example:

```
C:/Projects/blog/media/photo.jpg
```

---

### `MEDIA_URL`

works with the browser:

```
How does the user access it?
```

Example:

```
http://localhost:8000/media/photo.jpg
```

---

## One more important thing

In development, Django does **not automatically serve media files**.

You usually add this to your main `urls.py`:

```python
from django.conf import settings
from django.conf.urls.static import static


urlpatterns = [
    path('', include('shop.urls')),
]


if settings.DEBUG:
    urlpatterns += static(
        settings.MEDIA_URL,
        document_root=settings.MEDIA_ROOT
    )
```

This tells Django:

> "When someone visits `/media/...`, look inside the `media` folder."

So:

Browser request:

```
GET /media/profile.jpg
```

↓

Django checks:

```
MEDIA_ROOT/media/profile.jpg
```

↓

Returns:

```
profile.jpg
```

---

## The whole flow

```
User uploads image
        |
        ↓
ImageField
        |
        ↓
MEDIA_ROOT
        |
        ↓
media/products/image.jpg


Browser requests:

/media/products/image.jpg

        |
        ↓

MEDIA_URL

        |
        ↓

Django finds file in MEDIA_ROOT

        |
        ↓

Shows image
```

In short:

|Setting|Purpose|Example|
|---|---|---|
|`MEDIA_ROOT`|Where files are stored on your computer|`project/media/`|
|`MEDIA_URL`|URL used to access files in browser|`/media/`|

A good beginner rule to remember:

> **ROOT = where the file lives.**  
> **URL = how the user reaches it.**