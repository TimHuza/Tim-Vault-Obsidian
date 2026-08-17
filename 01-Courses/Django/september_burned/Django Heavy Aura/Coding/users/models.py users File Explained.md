#django 


```python
class User(AbstractUser):
```

means:

> "Create a new User model, but start with everything Django already has inside `AbstractUser`."

---

## 1. Creating the User model

```python
class User(AbstractUser):
```

Let's compare.

Django already has:

```
AbstractUser
      |
      |
      v
+----------------+
| username       |
| password       |
| email          |
| first_name     |
| last_name      |
| is_staff       |
| is_active      |
| permissions    |
+----------------+
```

When you write:

```python
class User(AbstractUser):
```

you are saying:

```
My User Model
      |
      |
      v
+----------------+
| username       |  <-- from AbstractUser
| password       |  <-- from AbstractUser
| email          |  <-- from AbstractUser
| first_name     |  <-- from AbstractUser
| last_name      |  <-- from AbstractUser
| image          |  <-- you add
+----------------+
```

You inherit all Django user features.

---

# 2. Adding a profile image

```python
image = models.ImageField(
    upload_to="users_image",
    blank=True,
    null=True
)
```

This creates a new database field called `image`.

Let's break it apart.

---

## `models.ImageField`

```python
models.ImageField()
```

This tells Django:

> "This field will store an image."

Example:

A user uploads:

```
profile.jpg
```

Django stores it in your media folder:

```
media/
   |
   └── users_image/
          |
          └── profile.jpg
```

---

## `upload_to="users_image"`

```python
upload_to="users_image"
```

This tells Django:

> "When a user uploads an image, put it inside a folder called users_image."

Example:

Before upload:

```
my_photo.png
```

After upload:

```
media/
└── users_image/
    └── my_photo.png
```

---

## `blank=True`

```python
blank=True
```

This affects **forms**.

It means:

> "The user does not have to upload an image."

Example:

Registration form:

```
Username: Tim
Password: *****
Image: _______
```

The image can be empty.

---

## `null=True`

```python
null=True
```

This affects the **database**.

It means:

> "The database is allowed to store an empty value."

Without `null=True`:

```
User Table

id | username | image
-------------------------
1  | Tim      | ????
```

Django says:

"Every user must have an image."

With:

```python
null=True
```

it allows:

```
User Table

id | username | image
-------------------------
1  | Tim      | NULL
```

---

## Why use both `blank=True` and `null=True`?

Because they control different things:

|Option|Controls|
|---|---|
|`blank=True`|Django forms|
|`null=True`|Database|

For images, you usually see both:

```python
image = models.ImageField(
    upload_to="users_image",
    blank=True,
    null=True
)
```

meaning:

> "Users do not need to upload a profile picture, and the database can leave it empty."

---

# 3. The Meta class

Now:

```python
class Meta:
```

Inside Django models, `Meta` is used to configure the model.

Think of it as:

```
User model
     |
     |
     +-- Fields
     |
     +-- Settings (Meta)
```

---

## Database table name

```python
db_table = "user"
```

This tells Django:

> "Use the database table name `user`."

Normally Django automatically creates:

```
appname_modelname
```

For example:

Your app:

```
accounts
```

Model:

```python
class User(AbstractUser):
```

Django might create:

```
accounts_user
```

But because you wrote:

```python
class Meta:
    db_table = "user"
```

Django creates:

```
user
```

instead.

---

Database:

```
user table
--------------------------------
id
username
password
email
first_name
last_name
image
```

---

# 4. The `__str__` method

Now:

```python
def __str__(self):
    return self.username
```

This controls how your object appears as text.

---

Imagine Django Admin.

Without `__str__`:

```
Users

<User: User object (1)>
<User: User object (2)>
<User: User object (3)>
```

Not very helpful.

---

With:

```python
def __str__(self):
    return self.username
```

You see:

```
Users

Tim
John
Sarah
```

Much better.

---

## How does `self.username` work?

Every user has a username.

Example:

```python
user.username
```

returns:

```
"Tim"
```

So:

```python
return self.username
```

returns:

```
Tim
```

---

# Full picture

Your model:

```python
class User(AbstractUser):
```

creates:

```
                AbstractUser
                     |
                     |
                     v
              Your User Model

+--------------------------------+
| id                             |
| username                       |
| password                       |
| email                          |
| first_name                     |
| last_name                      |
| is_staff                       |
| is_active                      |
|                                |
| image  <-- your new field      |
+--------------------------------+

Database table:
      |
      v
     user
```

---

# What happens when a user uploads an image?

Example:

User:

```
username: tim
password: 12345
image: tim.jpg
```

Django saves:

Database:

```
user table

id | username | image
----------------------------
1  | tim      | users_image/tim.jpg
```

File system:

```
media/
└── users_image/
       └── tim.jpg
```

---

## In simple words:

This code creates a **custom Django user** that:

1. Keeps all Django login features (`AbstractUser`)
    
2. Adds a profile picture (`ImageField`)
    
3. Stores users in a table called `user`
    
4. Shows usernames instead of "User object" in Django Admin
    

This is a very common pattern for **e-commerce websites, social media apps, and profile systems**.