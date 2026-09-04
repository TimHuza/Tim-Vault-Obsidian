#ai-agents-community 


## My First AI Project

I wanted to share my first AI project that I've made in early 2026. Today I understand that this is an easy project to do. But back then, for me as a beginner, it was definitely not easy for me.

AI Note Summarizer isn't an AI agent - it's a small local AI-powered summarization tool.

I built a small tool that takes your .txt, .md, or .pdf notes and asks a local LLM to summarize them for you — no cloud APIs, no data leaving your machine. Everything runs through Ollama with the `llama 3.1:8B` model, so once it's downloaded, the whole thing works offline.

Tech Stack:
- Python - main programming langauge
- Streamlit - for the UI
- LangChain - prompting, document processing, and connecting the application to Ollama
- Ollama - runs the Llama 3.1 8B model locally (you can use any model you want)

Project Structure:
- file_[loader.py](http://loader.py/ "http://loader.py") - loads and chunks input files
- [prompts.py](http://prompts.py/ "http://prompts.py") - defines three prompt styles (simple, detailed, exam)
- note_[engine.py](http://engine.py/ "http://engine.py") - appends saved summaries to data/notes.txt
- [ui.py](http://ui.py/ "http://ui.py") - the Streamlit entry point tying it all together.

Three Summarization Styles:
- Simple - gives you 3–5 short, plain-language bullet points, good for a quick refresher.
- Detailed - produces fuller bullets with explanations, useful when you actually need the nuance back.

- Exam - strips things down to dense facts, definitions, and key concepts.

UI:
In Enter Your File Name field you need to enter your file name with prefix. IMPORTANT thing, you need to add the file you want to summarize into `data` folder, otherwise it won't work for you! Then you select summarization style. Click on Summarize.

(It may take couple of seconds or a minute to give you a response! Then it save the summarized response into `notes.txt` file in `data` folder.)

Running it is simple:
1. Install Python 3.10+
2. Install Ollama, pull the model with "ollama pull llama3.1:8b" (make sure you have 4-5GB disk space)
3. Run "pip install -r requirements.txt"
4. Then run the project "streamlit run [ui.py](http://ui.py/ "http://ui.py")"

Drop your file into the "data" folder, type its name into the app, pick a style, hit Summarize and the summary appears right in the browser.