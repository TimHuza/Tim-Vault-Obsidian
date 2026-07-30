#django 

# Big Picture

Imagine you have an online toy store.

A customer comes to your website.

They click:

> 🧸 "Add Teddy Bear to Cart"

Somewhere, Django has to remember:

- Which products they added
    
- How many of each
    
- The price
    
- Calculate totals
    
- Remove items
    
- Empty the cart
    

That is exactly what this `Cart` class does.

---

# Before We Start

The cart is stored inside the **session**.

Think of a session like this:

```
Website
   │
   ▼
Visitor
   │
   ▼
Small private backpack
```

Every visitor gets their own invisible backpack.

Inside that backpack Django stores things like:

```
{
    "username": "Tim",
    "theme": "dark",
    "cart": {
        ...
    }
}
```

When the visitor leaves, Django still remembers everything inside that backpack until the session expires.

---

# Imports

```python
from decimal import Decimal
```

You already learned this one.

Instead of using normal floating numbers like

```
19.99
```

Python stores money using

```
Decimal("19.99")
```

because it is much more accurate for money.

---

```python
from django.conf import settings
```

This imports your Django settings.

For example inside `settings.py` you probably have

```python
CART_SESSION_ID = "cart"
```

So whenever you write

```python
settings.CART_SESSION_ID
```

it means

```
"cart"
```

instead of typing `"cart"` everywhere.

---

```python
from main.models import Product
```

This imports your Product model.

Later, the cart needs to load products from the database.

---

# The Cart Class

```python
class Cart:
```

This creates a blueprint for a shopping cart.

Every visitor gets their own Cart object.

Think of it like:

```
Visitor A
   │
   ▼
Cart()

Visitor B
   │
   ▼
Cart()

Visitor C
   │
   ▼
Cart()
```

Each visitor has their own cart.

---

# **init**()

```python
def __init__(self, request):
```

This runs automatically whenever you create a cart.

Example:

```python
cart = Cart(request)
```

Python immediately runs

```
__init__()
```

---

## Line 1

```python
self.session = request.session
```

Remember:

Every request contains the visitor's session.

```
Browser
    │
    ▼
Request
    │
    ▼
Session
```

Now

```
self.session
```

points to the visitor's session.

---

## Next

```python
cart = self.session.get(settings.CART_SESSION_ID)
```

Imagine the session looks like

```
Session
│
├── username
├── theme
└── cart
```

This line asks:

> "Does this visitor already have a cart?"

If yes:

```
cart =
{
    "3": {...},
    "8": {...}
}
```

If not

```
cart = None
```

---

## If there is no cart

```python
if not cart:
```

Suppose this is the visitor's first time.

Then

```
cart = None
```

so Python enters the block.

---

```python
cart = self.session[settings.CART_SESSION_ID] = {}
```

This creates an empty cart.

The session now becomes

```
Session

{
    "cart": {}
}
```

Empty dictionary.

---

Finally

```python
self.cart = cart
```

Now the class remembers the cart.

```
self.cart
```

points to

```
{}
```

---

# add()

```python
def add(self, product, quantity=1, override_quantity=False):
```

This function adds products.

Example

```python
cart.add(product)
```

or

```python
cart.add(product, quantity=5)
```

---

## Product ID

```python
product_id = str(product.id)
```

Suppose the product is

```
Laptop

id = 7
```

Then

```
product_id = "7"
```

Notice it becomes a string because dictionary keys are stored as strings.

---

## Check if already exists

```python
if product_id not in self.cart:
```

Suppose cart is

```
{}
```

Product 7 isn't there.

So create it.

---

```python
self.cart[product_id] = {
    'quantity': 0,
    'price': str(product.price)
}
```

Now cart becomes

```
{
    "7": {
        "quantity":0,
        "price":"999.99"
    }
}
```

Notice

```
price
```

is stored as a string.

Why?

Sessions save simple data types much more reliably than `Decimal` objects.

---

## Override quantity?

```python
if override_quantity:
```

Imagine cart already has

```
Laptop

Quantity = 2
```

If

```python
override_quantity=True
```

then

```python
cart.add(product, quantity=5, override_quantity=True)
```

becomes

```
Quantity = 5
```

Not

```
2 + 5
```

It replaces the value.

---

Otherwise

```python
else:
```

It adds to the current quantity.

```
Current

2
```

User adds one more

↓

```
3
```

because

```python
+= quantity
```

---

Finally

```python
self.save()
```

It tells Django

> "The cart changed."

---

# save()

```python
def save(self):
```

Only one line:

```python
self.session.modified = True
```

This tells Django:

> "Please save this updated session."

Without it, Django might think nothing changed.

Think of it like editing a document:

```
Old

Shopping List

Milk
Eggs
```

You add Bread.

If you never press Save...

```
Bread disappears.
```

`modified = True` is basically pressing Save.

---

# remove()

```python
def remove(self, product):
```

Gets product ID

```python
product_id = str(product.id)
```

If it exists

```python
del self.cart[product_id]
```

Dictionary before

```
{
 "3":{},
 "7":{},
 "9":{}
}
```

Delete 7

↓

```
{
 "3":{},
 "9":{}
}
```

Then save again.

---

# **iter**()

This is probably the hardest part of the file.

```python
def __iter__(self):
```

This allows you to write:

```python
for item in cart:
```

instead of doing complicated work yourself.

Python automatically calls `__iter__()` when you loop over an object.

---

## Product IDs

```python
product_ids = self.cart.keys()
```

Suppose

```
Cart

{
 "2":{},
 "5":{},
 "8":{}
}
```

Then

```
product_ids

["2","5","8"]
```

---

## Load products

```python
products = Product.objects.filter(id__in=product_ids)
```

This asks the database:

```
SELECT *

WHERE id IN (2,5,8)
```

It loads the real Product objects.

---

## Copy cart

```python
cart = self.cart.copy()
```

Instead of changing the original cart,

it makes a copy.

```
Original

↓

Copy
```

Safer.

---

## Attach products

```python
for product in products:
```

Suppose

```
Laptop
Mouse
Keyboard
```

Loop through each one.

---

```python
cart[str(product.id)]['product'] = product
```

Now each dictionary contains the actual Product object.

Before

```
{
 "7":{
     quantity:2,
     price:"999.99"
 }
}
```

After

```
{
 "7":{
     quantity:2,
     price:"999.99",
     product:<Laptop object>
 }
}
```

Now templates can do

```django
{{ item.product.name }}
```

because the whole product is attached.

---

## Convert price

```python
item['price'] = Decimal(item['price'])
```

Remember it was saved as

```
"999.99"
```

Now it becomes

```
Decimal("999.99")
```

so calculations are accurate.

---

## Calculate total

```python
item['total_price'] = item['price'] * item['quantity']
```

Example

```
Price

$20.00

Quantity

3
```

Total

```
$60.00
```

---

## yield

```python
yield item
```

`yield` is like saying:

> "Here's the next cart item. I'll remember where I stopped."

If your cart contains:

```
Laptop
Mouse
Keyboard
```

The loop behaves like:

```
1st iteration → Laptop
2nd iteration → Mouse
3rd iteration → Keyboard
```

instead of building one huge list all at once.

---

# **len**()

```python
def __len__(self):
```

This lets Python answer:

```python
len(cart)
```

Imagine

```
Laptop x2

Mouse x3

Keyboard x1
```

The code

```python
sum(item['quantity'] for item in self.cart.values())
```

adds:

```
2

+

3

+

1

=

6
```

So

```python
len(cart)
```

returns

```
6
```

meaning there are six items in total (counting quantities).

---

# clear()

```python
def clear(self):
```

Deletes the cart from the session.

```python
del self.session[settings.CART_SESSION_ID]
```

Before

```
Session

{
    "cart": {...}
}
```

After

```
Session

{}
```

Cart is completely gone.

---

# get_total_price()

This calculates the **grand total** of the cart after discounts.

The main calculation is:

```python
(Price - Discount) × Quantity
```

Let's use an example:

```
Price = $100
Discount = 20%
Quantity = 3
```

Step 1:

```
20% of $100 = $20
```

Step 2:

```
$100 − $20 = $80
```

Step 3:

```
$80 × 3 = $240
```

The `sum(...)` adds the totals for every product in the cart.

Finally:

```python
return format(total, '.2f')
```

Formats the result with two decimal places:

```
240
```

becomes

```
240.00
```

---

# Overall Flow

Here's the complete journey when a customer shops:

```text
Customer visits website
        │
        ▼
Cart(request)
        │
        ▼
Load cart from session
        │
        ▼
Customer clicks "Add to Cart"
        │
        ▼
add(product)
        │
        ▼
Save to session
        │
        ▼
Customer opens cart page
        │
        ▼
__iter__()
        │
        ├── Load Product objects
        ├── Convert prices to Decimal
        ├── Calculate each item's total
        └── Send items one by one to the template
        │
        ▼
Template displays cart
        │
        ▼
get_total_price()
        │
        ▼
Show final amount to pay
```

## What makes this class "Pythonic"?

Notice how the class defines special methods like `__init__`, `__iter__`, and `__len__`. These let your `Cart` object behave like a built-in Python collection:

- `Cart(request)` automatically initializes the cart (`__init__`).
    
- `for item in cart:` automatically calls `__iter__`.
    
- `len(cart)` automatically calls `__len__`.
    

This is one of the reasons Django code often feels natural to read—the framework and your own classes can work with Python's built-in features instead of requiring special method names like `get_items()` or `count_items()`.