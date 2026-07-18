#django 

# What is `<slug:slug>`?

This part:

```python
<slug:slug>
```

means:

> **"Take whatever text is in this part of the URL, make sure it looks like a slug, and give it to my view as a variable named `slug`."**

It has **two parts**:

```python
<slug:slug>
 ↑     ↑
type  variable name
```

- First `slug` → the **type** of data Django expects.
    
- Second `slug` → the **variable name** that will be passed to your view.
    

---

## Imagine this URL

```
https://mysite.com/iphone-16/
```

Django sees your URL pattern:

```python
path("<slug:slug>/", views.product_detail)
```

It matches like this:

```
URL
iphone-16
^^^^^^^^^

<slug:slug>
      ↑
slug = "iphone-16"
```

Then Django calls your view like this:

```python
product_detail(request, slug="iphone-16")
```

Your view might look like:

```python
def product_detail(request, slug):
    print(slug)
```

Output:

```
iphone-16
```

So Django automatically takes the text from the URL and gives it to your function.

---

# Why is it called a "slug"?

A slug is simply a URL-friendly version of some text.

For example:

Product name:

```
Apple iPhone 16 Pro Max
```

Slug:

```
apple-iphone-16-pro-max
```

Notice:

- lowercase
    
- spaces become `-`
    
- no strange characters
    

This makes URLs look nice.

Instead of

```
/product?id=42
```

you get

```
/apple-iphone-16-pro-max/
```

Much easier to read.

---

# What does the first `slug` mean?

The first one tells Django:

> "Only match text that looks like a slug."

A slug can contain things like:

```
hello
```

```
iphone-16
```

```
gaming-laptop
```

```
book-123
```

But not things like:

```
hello world
```

because spaces aren't allowed.

---

# What does the second `slug` mean?

The second one is simply the variable name.

You could write

```python
<slug:banana>
```

Then your view would be

```python
def product_detail(request, banana):
    print(banana)
```

If the URL is

```
/iphone-16/
```

Output:

```
iphone-16
```

So these are equivalent:

```python
<slug:slug>
```

```python
<slug:product_slug>
```

```python
<slug:banana>
```

The first `slug` **must** stay because it's the converter type, but the second can be almost any valid variable name.

---

# Step-by-step example

Suppose a user visits

```
/gaming-mouse/
```

### Step 1

The browser asks Django:

```
I want /gaming-mouse/
```

↓

### Step 2

Django checks every URL pattern.

First:

```python
path("", ...)
```

Doesn't match.

↓

Next:

```python
path("<slug:slug>/", ...)
```

Matches!

↓

### Step 3

Django extracts

```
gaming-mouse
```

and stores it as

```python
slug = "gaming-mouse"
```

↓

### Step 4

Django calls your view

```python
product_detail(request, slug="gaming-mouse")
```

↓

### Step 5

Inside the view

```python
def product_detail(request, slug):
    print(slug)
```

Output:

```
gaming-mouse
```

---

# Another example

URL:

```
/python-book/
```

Django does

```python
slug = "python-book"
```

Then

```python
product_detail(request, slug="python-book")
```

---

# One more example

URL:

```
/red-shirt/
```

Django calls

```python
product_detail(request, slug="red-shirt")
```

Your view can then find that product in the database:

```python
product = Product.objects.get(slug=slug)
```

Which becomes:

```python
product = Product.objects.get(slug="red-shirt")
```

Now Django knows exactly which product to display.

---

# Your category URL

You also have:

```python
path(
    "shop/category/<slug:category_slug>/",
    views.product_list,
    name="product_list_by_category"
)
```

Suppose the user visits

```
/shop/category/laptops/
```

Django extracts:

```python
category_slug = "laptops"
```

Then it calls

```python
product_list(request, category_slug="laptops")
```

Your view would be:

```python
def product_list(request, category_slug):
    print(category_slug)
```

Output:

```
laptops
```

---

# Beginner summary

Think of `<slug:slug>` as saying:

> **"Whatever text appears here in the URL, if it looks like a slug, save it in a variable called `slug` and pass it to my view."**

So:

```
URL
/products/iphone-16/
          │
          ▼
<slug:slug>
          │
          ▼
slug = "iphone-16"
          │
          ▼
product_detail(request, slug="iphone-16")
```

This is one of Django's **path converters**. The general pattern is:

```python
<type:variable_name>
```

Examples include:

- `<int:id>` → accepts integers like `42`
    
- `<str:name>` → accepts a text string without slashes
    
- `<slug:slug>` → accepts URL-friendly text like `iphone-16`
    
- `<uuid:pk>` → accepts UUID values
    
- `<path:file_path>` → accepts an entire path, including slashes
    

The idea is always the same: Django reads part of the URL, checks that it matches the specified type, and passes it to your view using the variable name you chose.