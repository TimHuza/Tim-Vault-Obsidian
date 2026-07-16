#django 


In Django templates, `|linebreaks` is a **template filter** that converts line breaks (`Enter` keys) in text into HTML paragraphs and line breaks.

Think of it as:

> "Take this plain text and make the new lines visible in the browser."

---

### Example without `|linebreaks`

Imagine your database has this text:

```
Hello my name is Tim.
I am learning Django.
This is my first project.
```

Your template:

```html
<p>{{ description }}</p>
```

Django will output:

```html
<p>
Hello my name is Tim.
I am learning Django.
This is my first project.
</p>
```

But HTML ignores normal line breaks, so the browser shows:

```
Hello my name is Tim. I am learning Django. This is my first project.
```

Everything becomes one line.

---

### Now using `|linebreaks`

Template:

```html
<p>{{ description|linebreaks }}</p>
```

Django converts it into HTML:

```html
<p>Hello my name is Tim.</p>
<p>I am learning Django.</p>
<p>This is my first project.</p>
```

The browser displays:

```
Hello my name is Tim.

I am learning Django.

This is my first project.
```

---

## How does `|` work?

The `|` symbol means:

> "Apply this filter to the value."

Example:

```html
{{ name|upper }}
```

If:

```python
name = "tim"
```

Output:

```
TIM
```

---

Another example:

```html
{{ text|linebreaks }}
```

means:

1. Take the variable `text`
    
2. Apply the `linebreaks` filter
    
3. Convert new lines into HTML
    
4. Display the result
    

---

## Common use case

Usually used for text fields from a database.

Example model:

```python
class Post(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()
```

User writes:

```
Today I learned Django.

It is really interesting.
```

Template:

```html
<h1>{{ post.title }}</h1>

<div>
    {{ post.content|linebreaks }}
</div>
```

The blog post keeps the formatting.

---

## Difference between `linebreaks` and `linebreaksbr`

Django has two similar filters:

### `linebreaks`

Creates paragraphs:

```html
{{ text|linebreaks }}
```

Output:

```html
<p>Hello</p>
<p>World</p>
```

---

### `linebreaksbr`

Only creates `<br>` tags:

```html
{{ text|linebreaksbr }}
```

Output:

```html
Hello<br>
World
```

---

For beginners, remember:

```
{{ variable|filter }}
```

means:

> "Take this variable and modify it before showing it."

So:

```
{{ post.content|linebreaks }}
```

means:

> "Show the post content, but preserve the user's line breaks."