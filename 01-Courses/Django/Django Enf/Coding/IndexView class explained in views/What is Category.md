#django 

This line:

```python
context["categories"] = Category.objects.all()
```

the `Category` here is almost certainly a **Django model**.

For example, somewhere in `models.py`, there might be code like this:

```python
from django.db import models

class Category(models.Model):
    name = models.CharField(max_length=100)
```

Here, the developer created a model named `Category`.

---

## What is a model?

A **model** is a Python class that represents a **table in the database**.

Imagine your database contains a table like this:

|id|name|
|---|---|
|1|Python|
|2|Django|
|3|AI|
|4|Cybersecurity|

This table is represented in Python by the `Category` model.

```
Database Table
+----+-----------------+
| id | name            |
+----+-----------------+
| 1  | Python          |
| 2  | Django          |
| 3  | AI              |
| 4  | Cybersecurity   |
+----+-----------------+

        ⇅

class Category(models.Model):
    name = models.CharField(...)
```

---

## Then what does this do?

```python
Category.objects.all()
```

Read it almost like an English sentence:

> "Category objects, give me all of them."

Django asks the database:

```
SELECT * FROM category;
```

and gets back all the rows.

---

## Why is it stored in `context`?

```python
context["categories"] = Category.objects.all()
```

Now the template can use those categories.

For example:

```html
<ul>
    {% for category in categories %}
        <li>{{ category.name }}</li>
    {% endfor %}
</ul>
```

The browser will display:

```text
• Python
• Django
• AI
• Cybersecurity
```

---

## Why is it called `Category`?

The name depends on the application.

For example:

- **Blog**
    
    - Python
        
    - Django
        
    - AI
        
- **Online store**
    
    - Electronics
        
    - Clothing
        
    - Books
        
- **Recipe website**
    
    - Breakfast
        
    - Lunch
        
    - Dinner
        

A "category" is simply a way to **group related items together**.

---

### In your code

When you see:

```python
Category.objects.all()
```

you should think:

> "Go to the database, get every category, and make them available to the HTML template."

So `Category` is **not built into Django**—it's a model (a Python class) that the developer created to represent a database table.