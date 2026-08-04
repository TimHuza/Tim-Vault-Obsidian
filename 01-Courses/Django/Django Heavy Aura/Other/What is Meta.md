#django 


> **The `Meta` class contains extra information (metadata) about your model, form, or other Django class.**

The word **Meta** literally means **"information about something."**

---

# Imagine a Student

Suppose you have a student.

The actual student has information like:

- name
    
- age
    
- grade
    

```python
class Student:
    name = "Tim"
    age = 15
```

But maybe the **school** also needs information **about the student**, for example:

- Which classroom is this student in?
    
- Should students be sorted alphabetically?
    
- What is the display name?
    

Those are **not properties of the student**.

They are **properties about the student.**

That is exactly what Django's `Meta` class is for.

---

# Example in Django

```python
class User(AbstractUser):

    class Meta:
        db_table = "user"
```

Notice that `Meta` is **inside** the `User` class.

```
User
│
├── username
├── password
├── email
│
└── Meta
    └── db_table = "user"
```

The `Meta` class isn't another model.

It simply tells Django:

> "Here are some special settings for this model."

---

# Why not put it directly in the class?

Imagine this:

```python
class User(AbstractUser):
    username = ...
    email = ...
    password = ...

    db_table = "user"
```

How would Django know whether `db_table` is:

- a database field?
    
- a normal Python variable?
    
- or a special Django option?
    

It would be confusing.

Instead, Django says:

> "Put all configuration inside `Meta`."

So Django knows exactly where to look.

---

# Think of it like a settings folder

Imagine your project is a video game.

```
Player
│
├── Health
├── Speed
├── Inventory
│
└── Settings
      ├── Difficulty
      ├── Max Players
      └── Spawn Point
```

The player has data.

The Settings describe **how the player behaves**.

`Meta` works the same way.

```
User
│
├── username
├── email
├── password
│
└── Meta
      ├── db_table
      ├── ordering
      ├── verbose_name
      └── permissions
```

---

# What kinds of things go inside `Meta`?

Here are some common options.

## 1. `db_table`

Choose the database table name.

```python
class Meta:
    db_table = "user"
```

Without it:

```
users_user
```

With it:

```
user
```

---

## 2. `ordering`

Automatically sort results.

```python
class Meta:
    ordering = ["username"]
```

Now when you do:

```python
User.objects.all()
```

Django automatically runs something like:

```
ORDER BY username
```

---

## 3. `verbose_name`

A nicer singular name.

```python
class Meta:
    verbose_name = "Customer"
```

Instead of Django displaying:

```
Users
```

it may display:

```
Customer
```

---

## 4. `verbose_name_plural`

Plural version.

```python
class Meta:
    verbose_name_plural = "Customers"
```

---

## 5. `permissions`

Create custom permissions.

```python
class Meta:
    permissions = [
        ("can_publish", "Can publish articles"),
    ]
```

---

## 6. `indexes`

Create database indexes to speed up searches.

```python
class Meta:
    indexes = [
        models.Index(fields=["username"]),
    ]
```

---

# How Django uses it

When Django starts your project, it reads your model.

```python
class User(AbstractUser):

    class Meta:
        db_table = "user"
        ordering = ["username"]
```

Django thinks something like:

```
I found a model called User.

Fields:
- username
- password
- email

Configuration:
- table name = user
- order by username
```

The fields become database columns.

The `Meta` class tells Django **how to work with those fields**.

---

# Does `Meta` create a table?

No.

It only provides instructions.

Think of it like this:

```
Model
│
├── Defines the data
│      username
│      email
│      password
│
└── Meta
       Defines how Django should treat that data
```

---

# Is `Meta` only used in models?

No! Django uses `Meta` in several places.

For example, in a **ModelForm**:

```python
class UserForm(forms.ModelForm):

    class Meta:
        model = User
        fields = ["username", "email"]
```

Here, `Meta` tells Django:

- which model the form is based on (`User`)
    
- which fields to include (`username`, `email`)
    

So the purpose is the same: **provide configuration**, but the available options depend on what you're configuring (a model, a form, etc.).

---

# Beginner summary

Think of every Django class as having **two parts**:

```
Model
│
├── Data
│      username
│      email
│      password
│
└── Meta
       Special settings for Django
```

A simple way to remember it is:

- **The main class** = _What is this object?_ (its data and behavior)
    
- **The `Meta` class** = _How should Django treat this object?_ (its configuration)
    

That's why you'll often see `Meta` used to specify things like the database table name, default ordering, human-readable names, and permissions without mixing those settings into the model's actual fields.