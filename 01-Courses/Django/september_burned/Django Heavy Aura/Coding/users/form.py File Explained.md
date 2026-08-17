#django 


- **Models (`models.py`)** = the database (where you store users, products, orders)
    
- **Views (`views.py`)** = the waiter (receives requests and gives responses)
    
- **Templates (`html`)** = the menu/page the customer sees
    
- **Forms (`forms.py`)** = the order form the customer fills out
    

A `forms.py` file is where we create and customize **HTML forms** and control how user input is handled.

For your `users` app:

```
users/
│
├── models.py       # User database model
├── views.py        # Login, register, profile logic
├── forms.py        # Login/register/profile forms
├── urls.py         # User URLs
└── templates/
    └── users/
        └── login.html
```

Your `forms.py` is responsible for creating a **login form**.

---

## 1. Imports

```Python
from django import forms
```

This imports Django's forms system.

Django gives us tools to create form fields:

Example:

```Python
username = forms.CharField()
password = forms.CharField()
```

Django will automatically create HTML like:

```html
<input type="text" name="username">

<input type="password" name="password">
```

Instead of manually writing HTML.

---

## 2. Import AuthenticationForm

```Python
from django.contrib.auth.forms import AuthenticationForm
```

Django already has a built-in login form called:

```
AuthenticationForm
```

It already knows how to:

- accept username
    
- accept password
    
- check if the user exists
    
- verify the password
    
- log the user in
    

Basically Django already wrote a login form for you.

It contains logic similar to:

```Python
username = input()
password = input()

check_database()

if password_is_correct:
    login_user()
```

So instead of creating a login form from zero:

```Python
class UserLoginForm(forms.Form):
```

you reuse Django's existing one:

```Python
class UserLoginForm(AuthenticationForm):
```

This is called **inheritance**.

---

# 3. Import your User model

```Python
from .models import User
```

The dot means:

```
from current app
```

So Django looks here:

```
users/models.py
```

and imports:

```Python
class User(AbstractUser):
```

Remember your previous code:

```Python
class User(AbstractUser):
    image = models.ImageField(...)
```

You created a custom User model.

Now your form needs to know:

"Which User model should this form work with?"

---

# 4. Creating your login form

```Python
class UserLoginForm(AuthenticationForm):
```

You are creating a new class:

```
UserLoginForm
```

but it inherits from:

```
AuthenticationForm
```

Meaning:

```
AuthenticationForm
        |
        |
        ↓
UserLoginForm
```

Your form automatically gets Django's login functionality.

---

# 5. Username field

```Python
username = forms.CharField()
```

This creates a username input.

It generates something like:

```html
<label>Username</label>
<input type="text" name="username">
```

`CharField` means:

"this field accepts text"

Example:

```
tim
john123
admin
```

---

# 6. Password field

```Python
password = forms.CharField()
```

Creates a password input.

Example HTML:

```html
<input type="text" name="password">
```

However, there is a problem.

A normal `CharField` creates a normal text box.

Meaning when you type:

```
mypassword123
```

the user sees:

```
mypassword123
```

Usually we want:

```
************
```

So normally we would write:

```Python
password = forms.CharField(
    widget=forms.PasswordInput()
)
```

which creates:

```html
<input type="password">
```

---

# 7. Meta class

```Python
class Meta:
```

The `Meta` class gives Django extra information about the form.

Think of it as settings for your form.

Example:

```
Form:
    What model does it use?
    Which fields should appear?
```

---

## 8. Connecting the form to your User model

```Python
model = User
```

This tells Django:

"This form is connected to my User model."

Your model:

```Python
class User(AbstractUser):
    image = models.ImageField(...)
```

So Django knows:

```
UserLoginForm
        |
        |
        ↓
users_user table
```

---

## 9. Selecting fields

```Python
fields = ["username", "password"]
```

This says:

"Only show these fields."

Your User model has many fields:

```
User
----------------
id
username
password
email
first_name
last_name
image
date_joined
last_login
```

But login only needs:

```
username
password
```

So we choose only those.

---

# How does everything work together?

Imagine a user visits:

```
example.com/login
```

## Step 1: View creates the form

`views.py`

```Python
def login_view(request):

    form = UserLoginForm()

    return render(
        request,
        "login.html",
        {"form": form}
    )
```

---

## Step 2: Template displays it

`login.html`

```html
<form method="POST">

{% csrf_token %}

{{ form }}

<button>
Login
</button>

</form>
```

Django generates:

```html
Username:
<input name="username">


Password:
<input name="password">
```

---

## Step 3: User submits

User enters:

```
username:
tim

password:
mypassword
```

Django receives:

```Python
{
 "username": "tim",
 "password": "mypassword"
}
```

---

## Step 4: AuthenticationForm checks

Django checks:

```
Does username exist?
        |
        YES

Is password correct?
        |
        YES

Login successful
```

---

# One thing I would improve in your code

Your current code:

```Python
class UserLoginForm(AuthenticationForm):
    username = forms.CharField()
    password = forms.CharField()
```

works, but I would normally write:

```Python
from django import forms
from django.contrib.auth.forms import AuthenticationForm


class UserLoginForm(AuthenticationForm):

    username = forms.CharField(
        widget=forms.TextInput(
            attrs={
                "placeholder": "Username"
            }
        )
    )

    password = forms.CharField(
        widget=forms.PasswordInput(
            attrs={
                "placeholder": "Password"
            }
        )
    )
```

Why?

Because now you can customize the HTML:

```html
<input placeholder="Username">

<input placeholder="Password">
```

and make it look better.

---

# In simple words

Your `forms.py` file:

- creates the boxes users type into
    
- validates the information
    
- connects user input with Django logic
    
- prevents writing repetitive HTML
    
- reuses Django's built-in authentication system
    

Your specific code means:

> "Create a custom login form for my custom User model. Use Django's existing login system, but define my username and password fields."

A common next step after this would be creating a **registration form** (`UserRegisterForm`) because login and registration usually work together in a `users` app.