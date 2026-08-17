#django 

# What is `csrf_token`?

`csrf_token` is a **secret security code** that Django uses to make sure that a form was submitted from **your website** and not from a fake or malicious website.

Think of it as a **secret password** that every form carries.

---

# Imagine this scenario 🏠

Let's say you have a website called:

```
https://myshop.com
```

You have a login form:

```html
<form method="POST">
    <input type="text" name="username">
    <input type="password" name="password">
    <button>Login</button>
</form>
```

A user logs in to your website.

---

## Now imagine an attacker 😈

The attacker creates another website:

```
https://evil-site.com
```

They secretly create a form like this:

```html
<form action="https://myshop.com/change-password/" method="POST">
    <input type="hidden" name="password" value="hacked123">
</form>

<script>
document.forms[0].submit();
</script>
```

If the user is already logged into **myshop.com**, their browser automatically sends their login cookies.

So Django might think:

> "Oh! The logged-in user wants to change their password."

Even though they never visited your website!

This attack is called **CSRF**.

---

# What does CSRF mean?

CSRF stands for:

> **Cross-Site Request Forgery**

Let's break that down.

- **Cross-Site** = coming from another website
    
- **Request** = sending data to your server
    
- **Forgery** = pretending to be the real user
    

So:

> Another website is pretending to be the real user.

---

# How Django prevents this

Whenever Django creates a form, it generates a random secret token.

Example:

```
8ad71b4ce9f7ea11a239d81...
```

When you write

```html
<form method="POST">
    {% csrf_token %}

    <input type="text">
</form>
```

Django secretly adds something like

```html
<input
    type="hidden"
    name="csrfmiddlewaretoken"
    value="8ad71b4ce9f7ea11a239d81..."
>
```

Notice that it is a **hidden input**.

The user never sees it.

---

# What the browser sends

When you press Submit, the browser sends

```
username=Tim
password=12345

csrfmiddlewaretoken=8ad71b4ce9f7ea11a239d81...
```

Django checks:

> "Is this secret token correct?"

If yes ✅

```
Allow the request.
```

If no ❌

```
Forbidden (403)
CSRF verification failed.
```

---

# Visual example

Without CSRF

```
Your Website
     │
     │ Login Form
     ▼
User clicks Submit
     │
     ▼
Server accepts request

Attacker Website
     │
     │ Fake Form
     ▼
Server ALSO accepts request 😱
```

---

With CSRF

```
Your Website
     │
     │ Secret Token
     ▼
User submits
     │
     ▼
Server checks token
     │
     ▼
✔ Token correct

------------------------

Attacker Website
     │
     │ No secret token
     ▼
Server checks token
     │
     ▼
❌ 403 Forbidden
```

---

# What does `{% csrf_token %}` actually do?

Suppose you write

```html
<form method="POST">
    {% csrf_token %}

    <button>Save</button>
</form>
```

Django turns it into something like

```html
<form method="POST">

<input
type="hidden"
name="csrfmiddlewaretoken"
value="4jH7Fd2A89dkL..."
>

<button>Save</button>

</form>
```

The hidden field is generated automatically.

---

# Why only POST?

You usually only need a CSRF token for requests that **change data**, such as:

- Creating a user
    
- Logging in
    
- Registering
    
- Updating a profile
    
- Deleting a product
    
- Changing a password
    

These are commonly sent using:

```html
method="POST"
```

You **don't** usually need it for a simple page request like:

```http
GET /products/
```

because viewing data doesn't change anything.

---

# Example in Django

### Template

```html
<form method="POST">
    {% csrf_token %}

    <input type="text" name="username">

    <button type="submit">
        Login
    </button>
</form>
```

---

### View

```python
from django.shortcuts import render

def login(request):
    if request.method == "POST":
        print(request.POST)

    return render(request, "login.html")
```

When the user clicks the button, Django automatically verifies the CSRF token **before** your view processes the request.

If the token is invalid or missing, Django returns a **403 Forbidden** response, and your `login()` view won't run.

---

# Why is it called a "token"?

A **token** is simply a unique piece of data used to prove something.

For example:

- A movie ticket proves you bought a seat.
    
- A concert wristband proves you're allowed inside.
    
- A hotel key card proves you're staying there.
    

A **CSRF token** proves:

> "This form came from my Django website."

---

# Beginner summary 📚

- `csrf_token` is a **security feature** in Django.
    
- It protects your website from **Cross-Site Request Forgery (CSRF)** attacks.
    
- It is added to forms using:
    

```html
{% csrf_token %}
```

- Django turns it into a hidden input containing a secret random value.
    
- When the form is submitted, Django checks that the token matches.
    
- If the token is missing or incorrect, Django blocks the request with **403 Forbidden**.
    
- You should include `{% csrf_token %}` in **every HTML form that uses `method="POST"`**.
    

As you continue learning Django, you'll notice that many tutorials include `{% csrf_token %}` in every POST form. It's one of those habits that's good to build early because it keeps your applications secure by default.