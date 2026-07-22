#django 



```python
page = request.GET.get('page', 1)

paginator = Paginator(products, 1)

current_page = paginator.page(int(page))

if current_slug:
	paginator = Paginator(products.filter(category=category), 1)
```

Let's go through it line by line.

---

# Step 1: Get the page number from the URL

```python
page = request.GET.get('page', 1)
```

## What is `request.GET`?

`request.GET` contains all the **query parameters** from the URL.

For example:

```
/products/?page=1
```

Django sees:

```python
request.GET
```

as something like

```python
{
    "page": "1"
}
```

Notice that `"1"` is a **string**, because everything in a URL is text.

---

### Example 1

URL:

```
/products/?page=2
```

Then

```python
page = request.GET.get("page", 1)
```

becomes

```python
page = "2"
```

---

### Example 2

URL:

```
/products/?page=5
```

Then

```python
page = "5"
```

---

### Example 3

URL:

```
/products/
```

There is **no** `page` parameter.

So

```python
request.GET.get("page", 1)
```

returns the default value:

```python
page = 1
```

That's what the second argument (`1`) is for.

It means:

> "If there is no `page` in the URL, use page 1."

---

# Step 2: Create the paginator

```python
paginator = Paginator(products, 1)
```

The syntax is:

```python
Paginator(objects, items_per_page)
```

Here:

```python
Paginator(products, 1)
```

means

> "Split this list into pages containing **1 item each**."

Imagine you have:

```
Product A
Product B
Product C
```

The paginator creates:

```
Page 1
--------
Product A
```

```
Page 2
--------
Product B
```

```
Page 3
--------
Product C
```

It **doesn't immediately choose a page**. It only prepares the pages.

Think of it like cutting a book into chapters.

```
All Products

↓
Paginator

Page 1
Page 2
Page 3
```

---

# Step 3: Select the page

```python
current_page = paginator.page(int(page))
```

Suppose the URL is

```
?page=2
```

Earlier we got

```python
page = "2"
```

Notice it's a string.

Before using it, the code converts it into an integer.

```python
int(page)
```

becomes

```python
2
```

Then Django does

```python
paginator.page(2)
```

This means

> "Give me page number 2."

The result is stored in

```python
current_page
```

Now

```python
current_page
```

contains **only the objects on page 2**.

---

# Visual example

Imagine there are four products.

```
A
B
C
D
```

Paginator:

```python
Paginator(products, 1)
```

creates

```
Page 1 → A

Page 2 → B

Page 3 → C

Page 4 → D
```

---

User opens

```
?page=3
```

Step 1:

```python
page = "3"
```

Step 2:

```python
int(page)
```

becomes

```
3
```

Step 3:

```python
current_page = paginator.page(3)
```

Now

```
current_page
```

contains

```
C
```

Only page 3 is returned.

---

# What is inside `current_page`?

Many beginners think

```python
current_page
```

is just a list.

It's actually a **Page object**.

It contains:

```
Current page number

Objects on this page

Previous page

Next page

Total pages

Has next?

Has previous?
```

So later in the template you can write things like

```django
{{ products.number }}
```

Current page number.

Or

```django
{% if products.has_next %}
```

Or

```django
products.next_page_number
```

---

# Why is `current_page` passed as `"products"`?

In your code:

```python
return render(
    request,
    "main/product/list.html",
    {
        "products": current_page,
    }
)
```

Notice the variable name changes.

Inside Python:

```python
current_page
```

Inside the template:

```django
products
```

So when the template loops:

```django
{% for product in products %}
```

it's actually looping over the **items in the current page**, not over the entire queryset.

---

# What happens when a category is selected?

Inside the `if` block, the same process happens again:

```python
paginator = Paginator(products.filter(category=category), 1)

current_page = paginator.page(int(page))
```

The only difference is **what is being paginated**.

Instead of paginating all available products, Django first creates a filtered list:

```
Filtered Products
```

Then it creates a new paginator:

```
Filtered Products
        │
        ▼
    Paginator
        │
        ▼
Page 1
Page 2
Page 3
```

Finally,

```python
current_page = paginator.page(int(page))
```

selects the requested page from the **filtered** results.

The pagination logic itself is **identical**—only the source list changes.

---

# Overall flow

Here's the complete flow of the pagination logic:

```
User visits

/products/?page=2
        │
        ▼
request.GET.get("page", 1)
        │
        ▼
page = "2"
        │
        ▼
int(page)
        │
        ▼
2
        │
        ▼
Paginator(products, 1)
        │
        ▼
Creates pages:
Page 1
Page 2
Page 3
...
        │
        ▼
paginator.page(2)
        │
        ▼
Returns a Page object containing only page 2's items
        │
        ▼
current_page
        │
        ▼
Sent to the template as "products"
        │
        ▼
Template displays only the items from page 2
```

One small note: in production code, you'll often see `paginator.get_page(page)` instead of `paginator.page(int(page))`. `get_page()` is more forgiving—it automatically handles missing, non-numeric, or out-of-range page numbers by returning a valid page instead of raising an exception.