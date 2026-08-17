#django 

# Step 1: Importing modules

```python
from django.db import models
from django.urls import reverse
```

### What is an import?

An import tells Python:

> "I want to use code that someone else already wrote."

It's similar to borrowing tools from a toolbox instead of making your own.

---

### First import

```python
from django.db import models
```

This imports Django's **database tools**.

Everything like:

- `CharField`
    
- `TextField`
    
- `ForeignKey`
    
- `DecimalField`
    
- `BooleanField`
    

comes from `models`.

Think of it like this:

```
models
│
├── CharField
├── TextField
├── IntegerField
├── ForeignKey
├── DateTimeField
└── ...
```

So later when Django sees

```python
models.CharField(...)
```

it knows exactly what `CharField` is.

---

### Second import

```python
from django.urls import reverse
```

We'll see this later:

```python
reverse(...)
```

Its job is to build URLs automatically.

Instead of writing

```
"/products/laptop/"
```

your code can ask Django:

> "Please give me the URL for this product."

---

# Step 2: Creating the Category model

```python
class Category(models.Model):
```

This creates a new Python class.

You already know classes in Python.

But this one is special.

Because it inherits from

```python
models.Model
```

it becomes a **database model**.

Think of a model as a blueprint.

For example:

```
Category
```

might represent this database table:

|id|name|slug|
|---|---|---|
|1|Electronics|electronics|
|2|Books|books|
|3|Shoes|shoes|

Every row is one Category object.

---

# Step 3: Category fields

---

## Name

```python
name = models.CharField(max_length=20, unique=True)
```

This creates a column in the database.

```
Category
----------------
id
name
slug
```

`CharField`

means:

> "Store short text."

Example:

```
Electronics
Books
Shoes
```

---

### max_length

```python
max_length=20
```

means

> Maximum 20 characters.

Examples:

✅ Books

✅ Electronics

❌ ThisCategoryNameIsWayTooLong

---

### unique=True

```python
unique=True
```

means

Every category name must be different.

Allowed:

```
Books
Shoes
Electronics
```

Not allowed:

```
Books
Books
```

The second one would cause an error.

---

# Slug

```python
slug = models.SlugField(max_length=20, unique=True)
```

A slug is text made for URLs.

Instead of

```
Gaming Laptop
```

you use

```
gaming-laptop
```

Instead of

```
Men Shoes
```

you use

```
men-shoes
```

Why?

Because URLs like

```
example.com/products/gaming-laptop
```

look much nicer.

---

# Step 4: Meta class

```python
class Meta:
```

This is **not another database table**.

It simply gives Django extra instructions.

Think of it as settings for this model.

---

## Ordering

```python
ordering = ['name']
```

Suppose the database contains

```
Shoes
Books
Electronics
```

Normally Django may return them in random order.

But because of

```python
ordering = ['name']
```

it automatically sorts them.

Result:

```
Books
Electronics
Shoes
```

---

## Indexes

```python
indexes = [
    models.Index(fields=['name'])
]
```

Imagine a book.

Without an index:

```
Find page 842...
```

You flip every page.

Slow.

With an index:

```
A → Page 15
B → Page 40
```

Much faster.

Database indexes work exactly like a book index.

If you search categories by name often,

```
Category.objects.get(name="Books")
```

the database can find them much faster.

---

## verbose_name

```python
verbose_name = "category"
```

Used mainly in Django Admin.

Instead of showing

```
Categorys
```

or some ugly automatic name,

it shows

```
Category
```

---

## verbose_name_plural

```python
verbose_name_plural = "categories"
```

Plural version.

Instead of

```
Categorys
```

Django displays

```
Categories
```

---

# Step 5: **str**()

```python
def __str__(self):
    return self.name
```

Suppose you have

```
Category
```

named

```
Books
```

Without `__str__`

printing it gives

```
<Category object (1)>
```

Very ugly.

With

```python
return self.name
```

printing it gives

```
Books
```

Much nicer.

---

# Step 6: Product model

```python
class Product(models.Model):
```

This creates another database table.

Imagine

|id|name|price|
|---|---|---|
|1|Laptop|999|
|2|Mouse|30|

---

# ForeignKey

```python
category = models.ForeignKey(
    Category,
    related_name='products',
    on_delete=models.CASCADE
)
```

This is one of the most important parts.

It creates a relationship.

Think of it like this:

```
Category
---------
Electronics

Products
---------
Laptop
Mouse
Keyboard
```

All three belong to Electronics.

Instead of storing

```
Electronics
```

inside every product,

the database stores the category ID.

Example:

Category table

|id|name|
|---|---|
|1|Electronics|

Product table

|id|name|category_id|
|---|---|---|
|5|Laptop|1|

So Product points to Category.

---

### related_name

```python
related_name="products"
```

Normally you can do

```python
category.product_set.all()
```

This changes it to

```python
category.products.all()
```

Much easier to read.

Imagine:

```
Books
```

Then

```python
books.products.all()
```

returns

```
Harry Potter
Lord of the Rings
Hobbit
```

---

### on_delete=models.CASCADE

Suppose you delete

```
Electronics
```

Should products stay?

Probably not.

CASCADE means

Delete category

↓

Automatically delete every product inside it.

---

# Name

```python
name = models.CharField(max_length=50)
```

Stores

```
Laptop
```

```
Keyboard
```

etc.

---

# Slug

```python
slug = models.SlugField(max_length=50)
```

For URLs

```
gaming-laptop
```

instead of

```
Gaming Laptop
```

---

# Image

```python
image = models.ImageField(
    upload_to='products/%Y/%m/%d',
    blank=True
)
```

Stores an image.

Example:

```
products/
    2026/
        07/
            15/
                laptop.jpg
```

The `%Y`, `%m`, and `%d` parts are replaced with the upload date (year, month, and day).

`blank=True`

means the image is optional.

---

# Description

```python
description = models.TextField(blank=True)
```

For long text.

Example

```
Gaming laptop with RTX graphics...
```

Unlike `CharField`, there is no maximum length unless you choose to add one.

---

# Price

```python
price = models.DecimalField(
    max_digits=10,
    decimal_places=2
)
```

Used for money.

Example:

```
19.99
```

Not

```
Float
```

because floats can lose precision.

---

# Available

```python
available = models.BooleanField(default=True)
```

Boolean means only

```
True
```

or

```
False
```

Example

```
Laptop

Available?

True
```

or

```
False
```

---

# Created

```python
created = models.DateTimeField(auto_now_add=True)
```

Automatically stores

```
2026-07-15 14:00
```

only once,

when the object is first created.

---

# Updated

```python
updated = models.DateTimeField(auto_now=True)
```

Updates automatically every time you save the product.

---

# Discount

```python
discount = models.DecimalField(
    default=0.00,
    max_digits=4,
    decimal_places=2
)
```

Example

```
10.00
```

means

```
10%
```

---

# Product Meta

```python
ordering = ['name']
```

Products come sorted alphabetically.

---

Indexes

```python
models.Index(fields=['id', 'slug'])
```

This speeds up searches using both `id` and `slug` together.

For example, if you frequently query:

```python
Product.objects.get(id=5, slug="gaming-laptop")
```

the database can find the row more efficiently.

Similarly,

```python
models.Index(fields=['name'])
```

helps when searching by name, and

```python
models.Index(fields=['-created'])
```

helps when listing the newest products first.

---

# **str**()

```python
return self.name
```

Instead of

```
<Product object>
```

you see

```
Laptop
```

---

# get_absolute_url()

```python
def get_absolute_url(self):
    return reverse(
        'main:product_detail',
        args=[self.slug]
    )
```

This asks Django:

> "Generate the correct URL for this product."

If the slug is

```
gaming-laptop
```

the result might be

```
/products/gaming-laptop/
```

You don't hard-code the URL yourself—`reverse()` looks up your URL configuration and builds it for you.

---

# sell_price()

```python
def sell_price(self):
```

This calculates the final price after a discount.

---

If there is a discount:

```python
if self.discount:
```

For example:

```
Price

100

Discount

20
```

Then:

```python
self.price * (self.discount / 100)
```

becomes

```
100 × 20%

=

20
```

Then

```python
100 - 20
```

becomes

```
80
```

Finally:

```python
round(..., 2)
```

rounds the result to two decimal places:

```
80.00
```

---

If there is **no discount** (`discount` is `0`), the `if` condition is false, so the method simply returns the original price:

```python
return self.price
```

For example:

```
Price:    100.00
Discount: 0.00

Result:   100.00
```

---

# The complete database structure

After Django creates the tables, you can imagine them like this:

```
Category
-----------------------------------
id
name
slug


Product
-----------------------------------
id
category_id  ───────────────┐
name                        │
slug                        │
image                       │
description                 │
price                       │
available                   │
created                     │
updated                     │
discount                    │
                             │
                             ▼
                    Category.id
```

This line shows that every product belongs to exactly one category through the `category_id` foreign key. One category can have many products, which is called a **one-to-many relationship**.