#django

Consider this code:

```python
def home(request):
    return render(request, "home.html")
```

## What is `request`?

`request` is **the user's request to your website**.

Think of it like this:

> A visitor knocks on your website's door and says,  
> "Hi, I'd like to see the Home page."

That "knock" is the **request**.

---

## Real-life analogy

Imagine you own a restaurant.

A customer walks in and says:

> "I'd like a pizza."

The customer's order is the **request**.

Then you prepare the pizza and give it back.

The pizza is the **response**.

Exactly the same thing happens in Django.

```
Browser
   │
   │ "Please show me the home page."
   ▼
request
   │
   ▼
home(request)
   │
   │ Creates a response
   ▼
response
   │
   ▼
Browser displays the page
```

---

## Step by step

Suppose someone visits:

```
http://127.0.0.1:8000/
```

The browser sends a request to Django.

Django calls your function:

```python
def home(request):
```

Notice that Django automatically passes the request object into your function.

So it's almost like Django is doing this behind the scenes:

```python
request = HttpRequest(...)
home(request)
```

You don't create `request` yourself.

Django creates it and gives it to your view.

---

## What is inside `request`?

The `request` object contains information about the visitor.

For example:

- Which page they requested
    
- Which HTTP method they used (`GET`, `POST`, etc.)
    
- Form data they submitted
    
- Cookies
    
- Logged-in user
    
- Headers
    
- Much more
    

Think of it as a **box full of information** about the visitor.

```
request
│
├── page requested
├── GET data
├── POST data
├── cookies
├── logged-in user
├── browser information
└── ...
```

---

## Why do we pass it to `render()`?

```python
return render(request, "home.html")
```

Even though you're only rendering a template, Django still wants to know **which request** this page belongs to.

So you pass the same request object along.

---

## A simple flow

```
1. User visits your website
            │
            ▼
2. Browser sends a request
            │
            ▼
3. Django creates a request object
            │
            ▼
4. Django calls

def home(request):

            │
            ▼
5. Your function returns HTML

return render(request, "home.html")

            │
            ▼
6. Browser receives the page
```

---

## An important thing to remember

You never call this function yourself like this:

```python
home(request)
```

Instead, Django does it for you.

When someone visits your website:

```
Browser
    │
    ▼
Django
    │
    ▼
home(request)
```

---

## Beginner summary

```python
def home(request):
    return render(request, "home.html")
```

- `home` is your view function.
    
- `request` is an object created by Django that represents **the user's request**.
    
- Django automatically passes the `request` object into your function.
    
- Your function uses that request and returns a response (in this case, the `home.html` page).
    

A simple way to remember it is:

> **Request comes in → Your view processes it → Response goes back to the browser.**

That's the basic request-response cycle that every Django application is built around.