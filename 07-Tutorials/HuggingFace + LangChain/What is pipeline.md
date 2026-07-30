#tutorial

# What is `pipeline`?

When you write:

```python
from transformers import pipeline
```

you're importing a **helper function** from the Hugging Face Transformers library.

A **pipeline** is a **ready-to-use AI workflow**.

Instead of building an AI model piece by piece, `pipeline()` does almost everything for you.

Think of it like this:

- Without `pipeline` → You have to build a car from thousands of parts.
    
- With `pipeline` → Someone gives you a fully assembled car. You just drive it.
    

---

# Without `pipeline`

Imagine you wanted an AI to answer questions.

Normally you'd have to:

1. Download the model.
    
2. Download the tokenizer.
    
3. Convert text into numbers.
    
4. Send those numbers into the model.
    
5. Convert the output back into text.
    

Something like this:

```python
from transformers import AutoTokenizer, AutoModelForQuestionAnswering

tokenizer = AutoTokenizer.from_pretrained("...")
model = AutoModelForQuestionAnswering.from_pretrained("...")

# tokenize text
# run model
# decode answer
```

Lots of code.

---

# With `pipeline`

You simply write:

```python
from transformers import pipeline

qa = pipeline("question-answering")
```

Done!

Now you already have a working AI.

---

# Think of `pipeline` as a machine

Imagine a factory.

```
Question
   │
   ▼
+--------------------+
|     pipeline()     |
|                    |
| Tokenizer          |
| AI Model           |
| Output Formatter   |
+--------------------+
   │
   ▼
Answer
```

The pipeline hides all the complicated work.

---

# What happens inside?

When you call:

```python
classifier = pipeline("sentiment-analysis")
```

Hugging Face automatically:

```
Step 1
Download the model
        │
        ▼
Step 2
Download the tokenizer
        │
        ▼
Step 3
Prepare your text
        │
        ▼
Step 4
Run the AI model
        │
        ▼
Step 5
Convert prediction into readable text
        │
        ▼
Return result
```

You only see one line of code.

---

# Different kinds of pipelines

The first argument tells Hugging Face **what task you want the AI to perform**.

## Text generation

```python
generator = pipeline("text-generation")
```

Example:

```python
generator("Once upon a time")
```

Output:

```
Once upon a time there was a dragon...
```

---

## Sentiment analysis

```python
classifier = pipeline("sentiment-analysis")
```

Example:

```python
classifier("I love pizza!")
```

Output:

```python
[
    {
        "label": "POSITIVE",
        "score": 0.999
    }
]
```

---

## Translation

```python
translator = pipeline("translation")
```

Example:

```python
translator("Hello")
```

↓

```
Bonjour
```

---

## Summarization

```python
summarizer = pipeline("summarization")
```

Example:

```python
summary = summarizer(long_article)
```

↓

```
Short summary...
```

---

## Question answering

```python
qa = pipeline("question-answering")
```

Example:

```python
qa(
    question="What is Python?",
    context="Python is a programming language."
)
```

↓

```
Python is a programming language.
```

---

## Image classification

```python
classifier = pipeline("image-classification")
```

Input:

```
📷 Dog picture
```

↓

Output:

```
Golden Retriever
99.2%
```

---

# Why is it called a "pipeline"?

In engineering, a **pipeline** is a sequence of steps where the output of one step becomes the input to the next.

For example:

```
Dirty water
    │
    ▼
Filter
    │
    ▼
Cleaner water
    │
    ▼
Purifier
    │
    ▼
Clean drinking water
```

The same idea applies in AI:

```
Text
   │
   ▼
Tokenizer
   │
   ▼
AI Model
   │
   ▼
Decoder
   │
   ▼
Final Answer
```

Everything flows through the pipeline.

---

# Why beginners love `pipeline`

Without `pipeline`:

```python
Tokenizer
↓
Model
↓
Inputs
↓
Outputs
↓
Decode
↓
Postprocess
```

Many lines of code.

With `pipeline`:

```python
from transformers import pipeline

chatbot = pipeline("text-generation")
```

Just one line.

---

# A simple mental model

Think of `pipeline` as a **smart assistant**.

You tell it:

> "I want to translate text."

It automatically:

- Picks the right tokenizer.
    
- Loads the appropriate model (or the one you specify).
    
- Prepares your input.
    
- Runs the model.
    
- Returns the result in an easy-to-use format.
    

Instead of managing all the individual pieces yourself, you interact with one object.

---

## Example

```python
from transformers import pipeline

classifier = pipeline("sentiment-analysis")

result = classifier("This movie was amazing!")

print(result)
```

Output:

```python
[
    {
        "label": "POSITIVE",
        "score": 0.9998
    }
]
```

Here:

- `pipeline` creates a sentiment analysis pipeline.
    
- `classifier` is the pipeline object.
    
- Calling `classifier("This movie was amazing!")` sends your text through all the necessary steps and returns the prediction.
    

As you become more experienced with Hugging Face, you'll often use `AutoTokenizer` and `AutoModel` directly for greater control. But `pipeline()` is the easiest and fastest way to start experimenting with AI models.