#django 

# What is `Paginator`?

Imagine you have a library with **1,000 books**.

If someone asks:

> "Show me all the books."

Would you carry all **1,000 books** to the table?

😂 That would be impossible.

Instead, you say:

> "Here are the first 20 books."
> 
> "When you're done, press **Next** to see the next 20."

That is exactly what **Paginator** does.

It **splits a large list into smaller pages.**

Instead of showing every object at once, Django shows only a few.

---

# Why do we need it?

Imagine your database contains:

```
Products
--------
Laptop
Mouse
Keyboard
Phone
...
50,000 more products
```

If Django did:

```python
products = Product.objects.all()
```

and your template displayed every product...

```
Laptop
Mouse
Keyboard
Phone
...
50,000 more
```

Problems:

- 🐌 Page loads very slowly.
    
- 💾 Uses lots of memory.
    
- 📱 User has to scroll forever.
    
- 🌐 More data is sent over the internet.
    

Instead, websites usually show something like:

```
Products

Laptop
Mouse
Keyboard
Phone
Tablet
...

< Previous | 1 | 2 | 3 | 4 | Next >
```

Only maybe **10 or 20 products** are shown at once.

---

# What is `Paginator`?

`Paginator` is a Django class that takes a list (or QuerySet) and divides it into pages.

Example:

```python
from django.core.paginator import Paginator

products = Product.objects.all()

paginator = Paginator(products, 10)
```

This means:

> "Take all products and put **10 products on each page**."

---

# Visual Example

Suppose your products are

```
1 Apple
2 Banana
3 Orange
4 Pear
5 Kiwi
6 Mango
7 Peach
8 Lemon
9 Cherry
10 Plum
11 Grape
12 Melon
13 Coconut
14 Lime
15 Pineapple
```

Now create

```python
Paginator(products, 5)
```

Django divides them into:

```
Page 1
------
Apple
Banana
Orange
Pear
Kiwi
```

```
Page 2
------
Mango
Peach
Lemon
Cherry
Plum
```

```
Page 3
------
Grape
Melon
Coconut
Lime
Pineapple
```

---

# How does it work?

## Step 1

Get all products.

```python
products = Product.objects.all()
```

Think of this as a huge box of products.

```
📦
Apple
Banana
Orange
Pear
...
```

---

## Step 2

Create a paginator.

```python
paginator = Paginator(products, 5)
```

Now Django cuts the box into pages.

```
📄 Page 1
Apple
Banana
Orange
Pear
Kiwi

📄 Page 2
Mango
Peach
...

📄 Page 3
...
```

---

## Step 3

Find out which page the user wants.

Imagine the URL:

```
/products/?page=2
```

The browser is saying:

> "Please show page 2."

You get that with

```python
page_number = request.GET.get("page")
```

If the URL is

```
?page=2
```

then

```python
page_number
```

equals

```
"2"
```

---

## Step 4

Ask the paginator for that page.

```python
page_obj = paginator.get_page(page_number)
```

If the user requested page 2:

```
page_obj
```

contains

```
Mango
Peach
Lemon
Cherry
Plum
```

instead of every product.

---

# Complete Example

```python
from django.core.paginator import Paginator

def product_list(request):
    products = Product.objects.all()

    paginator = Paginator(products, 10)

    page_number = request.GET.get("page")

    page_obj = paginator.get_page(page_number)

    return render(request, "products.html", {
        "page_obj": page_obj
    })
```

---

# In the template

You can loop just like normal.

```html
{% for product in page_obj %}
    {{ product.name }}
{% endfor %}
```

Only the current page's products are shown.

---

# Navigation Buttons

You can build buttons like this.

```html
{% if page_obj.has_previous %}
    <a href="?page={{ page_obj.previous_page_number }}">
        Previous
    </a>
{% endif %}
```

Current page:

```html
Page {{ page_obj.number }}
```

Next button:

```html
{% if page_obj.has_next %}
    <a href="?page={{ page_obj.next_page_number }}">
        Next
    </a>
{% endif %}
```

If you're on page 3:

```
Previous   Page 3   Next
```

---

# What does `page_obj` contain?

Besides the objects themselves, it has useful information:

```python
page_obj.number
```

Current page number.

Example:

```
2
```

---

```python
page_obj.has_next()
```

Returns

```
True
```

or

```
False
```

Example:

```
Page 2 → True
Page 10 → False
```

---

```python
page_obj.has_previous()
```

Returns

```
True
```

or

```
False
```

Example:

```
Page 1 → False
Page 2 → True
```

---

```python
page_obj.next_page_number()
```

Returns

```
3
```

---

```python
page_obj.previous_page_number()
```

Returns

```
1
```

---

```python
page_obj.paginator.num_pages
```

Returns the total number of pages.

Example:

```
150 products

10 per page

150 / 10 = 15 pages
```

Result:

```
15
```

---

```python
page_obj.paginator.count
```

Returns the total number of objects.

Example:

```
150
```

---

# What does the URL look like?

Page 1

```
/products/?page=1
```

Page 2

```
/products/?page=2
```

Page 15

```
/products/?page=15
```

The only thing changing is the `page` query parameter.

---

# Behind the scenes

Suppose there are **1,000 products**, and each page shows **10**.

When the user visits:

```
?page=3
```

The paginator calculates:

```
Page size = 10

Start = (3 − 1) × 10 = 20
End = 30
```

So it returns products **21–30**.

```
Products

1
2
...
20

21 ✅
22 ✅
23 ✅
24 ✅
25 ✅
26 ✅
27 ✅
28 ✅
29 ✅
30 ✅

31
32
...
1000
```

Only those 10 products are displayed on that page.

---

# Summary

`Paginator` helps you display large collections of data in manageable pages.

The typical flow is:

1. Retrieve all objects from the database.
    
2. Create a `Paginator` with a chosen page size.
    
3. Read the requested page number from the URL (`request.GET`).
    
4. Use `get_page()` to retrieve the correct page.
    
5. Pass the resulting `page_obj` to the template.
    
6. Loop over `page_obj` and use its helper methods (`has_next`, `has_previous`, etc.) to build page navigation.
    

Without `Paginator`, a page might try to render thousands of records at once, making it slow and difficult to use. With `Paginator`, users see a small, fast-loading page of results and can navigate using **Previous**, **Next**, or page number links.