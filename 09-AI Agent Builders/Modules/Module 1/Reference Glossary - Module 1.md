#ai-agents-community 


Use this section when a future lesson mentions a term. **You do not need to memorize it today.**

## AI basics

- **LLM (large language model):** a model trained on huge amounts of text so it can understand and produce language. Many assistants use LLMs, but future lessons may also use models that handle images, audio, or other data.
    
- **Token:** a small chunk of text the model reads or writes. Tokens affect cost and how much fits in the context window.
    
- **Hallucination:** when a model states something false with confidence. This is why important work needs verification.
    
- **Model provider:** a company that gives access to models, such as OpenAI, Anthropic, Google, and others.
    
- **Human in the loop:** a checkpoint where the agent stops and waits for your approval before it does something it can't undo. Send, pay, delete.
    
- **Orchestration:** A system or agent that coordinates multiple tools, agents, models, and steps within a workflow. It decides what should happen next and directs each part of the system.
    
- **Plugin:** An add-on that extends the capabilities of an AI agent or application by providing additional tools, instructions, or integrations.
    
- **Connector:** A bridge that links an AI system to an external service or data source, such as Gmail, Slack, or Google Drive. Connectors commonly use APIs or OAuth to control what the AI can access and do.
    
- **AI Bias / Model Bias:** A systematic tendency in an AI system that can produce distorted, unbalanced, or unfair results. Bias can come from training data, model design, human decisions, or how the system is used.
    
- **Agent Framework:** A toolkit that helps developers build and manage AI agents, including their tools, workflows, memory, decisions, and interactions. LangChain and LangGraph are examples of agent frameworks.
    
- **Retrieval-Augmented Generation (RAG):** An AI technique that retrieves relevant information from external sources, such as documents or databases, and gives it to the model as context before it generates an answer.
    
- **AI agent harness:** is the software infrastructure and environment wrapped around a large language model (LLM) to turn it into an autonomous work engine. Expressed as a simple equation: Agent = Model + Harness. The model provides the core intelligence ("brain"), while the harness provides the tools, execution loops, memory, and safety guardrails ("hands and environment") needed to accomplish real-world tasks.
    

## Your machine and your server

- **Terminal:** the text window where you type commands. In this course, commands are provided for you to copy and paste.
    
- **Command:** a single instruction you give a computer through the terminal.
    
- **Server:** a computer that stays on and runs programs around the clock.
    
- **VPS (virtual private server):** a rented server in a data center. It lets your worker run even when your own computer is off.
    
- **Local:** running software on your own computer instead of on a server.
    
- **Deploy:** put the worker somewhere it can run for real.
    
- **GPU:** A Graphical Processing Unit is a module that can be added to a computer to perform AI tasks (or video game) faster than the computer's alone. A GPU normally provides a connection for a video monitor.
    

## Security and secrets

- **SSH:** a secure way to log into a server from your computer.
    
- **SSH key:** a digital key that proves it is you when you connect to a server. Safer than a password.
    
- **Firewall:** a filter that blocks connections to your server except the ones you allow.
    
- **File permissions:** rules for who can read, change, or run each file.
    
- **Backup:** a saved copy of your files so a mistake or crash does not wipe out your work.
    
- **Environment variable:** a named value stored on your machine that programs can read, often used for secrets like API keys.
    
- **API key:** a credential that lets software use a service. _Treat it like a password._
    
- **Secret:** any credential that must not be shared, such as passwords, API keys, and tokens.
    
- **Prompt injection:** malicious or misleading instructions hidden inside content the worker reads, such as an email or webpage. A safe worker treats outside content as _data_, not as _orders_.
    

## Files and versions

- **Git:** a tool that tracks versions of files.
    
- **Commit:** a saved snapshot in git. _Never commit secrets._
    
- **Markdown:** a simple text format used for notes and agent files.
    
- **File tree:** the folder structure your worker uses. Organized files help an agent find the right information.
    

## The brain

- **Obsidian:** a notes app that stores files in plain text. It can be used as a simple business brain for an agent.
    
- **Vault:** Obsidian's name for a folder of notes.
    
- **Brain:** a structured set of notes about you, your business, your projects, and your rules.
    
- **Skill:** a saved instruction an agent can reuse for a specific job.
    

## Connections

- **Gateway:** a channel you use to reach your worker, such as Telegram, Slack, web chat, or email.
    
- **MCP (Model Context Protocol):** a standard way to connect AI systems with tools and data. Think of it as one common connection pattern instead of a custom setup every time.
    
- **Connector Platform:** a prebuilt connection to a tool or service, often provided by platforms like Zapier or Composio.
    

## Running on autopilot

- **Schedule:** a rule for when something runs, such as every morning at 7:00 AM.
    
- **Cron:** a common scheduling system on servers. A cron job is a task that runs on a timer.
    
- **Caching:** reusing work that was already done instead of paying or waiting to do it again.
    
- **Rate limit:** a cap on how much you can use a service within a period of time.
    
- **Automation:** a task that now happens without you manually doing each step.
    

## Your first worker

- **VA (virtual assistant):** in this course, a first useful worker that handles daily summaries, inbox triage, updates, or other routine business tasks.
    
- **Inbox triage:** sorting email into what needs you, what can wait, what can be archived, and what needs a draft reply.
    

## Action step

> **_Post in the community:_** _share additional words and their meanings that we may have missed in this glossary!_