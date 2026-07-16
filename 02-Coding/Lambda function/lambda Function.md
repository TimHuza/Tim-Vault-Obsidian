#coding

# What is a `lambda` function?

A **lambda function** is simply a **small function without a name**.

Normally, when you create a function, you give it a name.

Example:

```python
def add(a, b):
    return a + b
```

Here,

- function name → `add`
    
- parameters → `a`, `b`
    
- returns → `a + b`
    

You can call it like this:

```python
print(add(2, 3))
```

Output:

```
5
```

---

## A lambda does the exact same thing

Instead of writing:

```python
def add(a, b):
    return a + b
```

you can write

```python
add = lambda a, b: a + b
```

This creates a function and stores it in the variable `add`.

Now:

```python
print(add(2, 3))
```

Output

```
5
```

So these two are **equivalent**:

```python
def add(a, b):
    return a + b
```

and

```python
add = lambda a, b: a + b
```

---

# Let's break down the syntax

Suppose you have

```python
lambda x: x * 2
```

Break it into pieces:

```
lambda
```

means

> "I'm creating a function."

---

```
x
```

means

> "This function accepts one parameter named x."

---

```
:
```

means

> "Everything after this is what the function returns."

---

```
x * 2
```

means

> "Return x multiplied by 2."

So

```python
lambda x: x * 2
```

is exactly the same as

```python
def double(x):
    return x * 2
```

---

# Example 1

Normal function

```python
def square(x):
    return x * x
```

Lambda

```python
square = lambda x: x * x
```

Using it

```python
print(square(4))
```

Output

```
16
```

---

# Example 2

Normal function

```python
def greet(name):
    return "Hello " + name
```

Lambda

```python
greet = lambda name: "Hello " + name
```

Using it

```python
print(greet("Tim"))
```

Output

```
Hello Tim
```

---

# Example 3

Multiple parameters

Normal function

```python
def multiply(a, b):
    return a * b
```

Lambda

```python
multiply = lambda a, b: a * b
```

Using it

```python
print(multiply(3, 5))
```

Output

```
15
```

---

# Why is it called an anonymous function?

Because it **doesn't have its own name**.

Normally:

```python
def add(a, b):
```

The function's name is `add`.

With lambda:

```python
lambda a, b: a + b
```

There is **no name**.

You can later store it in a variable:

```python
add = lambda a, b: a + b
```

Now the variable `add` refers to that anonymous function.

---

# Why use lambda?

Imagine you only need a function **once**.

Instead of writing

```python
def square(x):
    return x * x
```

you can simply write

```python
lambda x: x * x
```

Python programmers often use lambdas when passing functions to other functions.

For example:

```python
numbers = [1, 2, 3, 4]

result = list(map(lambda x: x * 2, numbers))

print(result)
```

Output

```
[2, 4, 6, 8]
```

Here, `map()` needs a function that tells it **what to do with each number**. Instead of defining a separate function, we provide a lambda directly.

---

# Comparing `def` and `lambda`

### Using `def`

```python
def double(x):
    return x * 2

print(double(5))
```

---

### Using `lambda`

```python
double = lambda x: x * 2

print(double(5))
```

Both print

```
10
```

---

# Important limitation

A lambda can only contain **one expression**.

This is allowed:

```python
lambda x: x + 1
```

This is **not** allowed:

```python
lambda x:
    y = x + 1
    return y
```

If your function needs multiple statements, use `def` instead.

---

# An easy way to remember

Think of `lambda` like this:

```
lambda parameters: value_to_return
```

or mentally translate it to:

> **"Create a small function that takes these parameters and returns this value."**

For example:

```python
lambda x: x * 2
```

means

> "Create a function that takes `x` and returns `x * 2`."

---

As a beginner, you don't need to use `lambda` often. Most Python code for learning is easier to read with `def`. Once you're comfortable with functions, you'll start seeing `lambda` used with functions like `map()`, `filter()`, and `sorted()`, where it makes the code shorter and more convenient.