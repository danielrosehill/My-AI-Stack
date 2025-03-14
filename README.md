# My AI Stack

![alt text](banner.webp)

[![Last Updated](https://img.shields.io/badge/Last%20Updated-March%2014%2C%202025-blue)](https://github.com/your-repo)
[![Status](https://img.shields.io/badge/Status-Evolving-brightgreen)](https://github.com/your-repo)
[![Focus](https://img.shields.io/badge/Focus-Productivity-orange)](https://github.com/your-repo)
[![Docker](https://img.shields.io/badge/Docker-Compose-blue)](https://github.com/your-repo)

This document outlines my current AI stack and the tools I use regularly. Given the rapid evolution of the AI landscape, this stack is constantly evolving. I'm always tinkering and experimenting, but these are the components I've found particularly valuable for enhancing my productivity. You can find out more about my AI projects and thoughts on my [homepage](https://danielrosehill.com/).

## Table of Contents

- [My AI Stack](#my-ai-stack)
  - [Table of Contents](#table-of-contents)
  - [Core AI Components](#core-ai-components)
    - [LLM APIs](#llm-apis)
    - [LLM Frontend](#llm-frontend)
    - [Speech To Text / ASR](#speech-to-text--asr)
    - [Vector Storage](#vector-storage)
    - [Regular Storage](#regular-storage)
  - [Agentic, Generative \& Orchestration Tools](#agentic-generative--orchestration-tools)
    - [Agents, Assistants](#agents-assistants)
    - [Other Generative AI](#other-generative-ai)
      - [Text To Image](#text-to-image)
      - [Text To Video](#text-to-video)
    - [Workflows / Orchestration](#workflows--orchestration)
    - [Agentic Workflows \& Tools](#agentic-workflows--tools)
      - [AI IDEs](#ai-ides)
      - [Computer Use](#computer-use)
  - [Docker Implementation](#docker-implementation)
  - [APIs](#apis)

## Core AI Components

These are the foundational elements of my AI stack. They represent the key technologies and infrastructure that support most of my AI-related activities.

### LLM APIs

I heavily rely on LLMs via API, preferring them over self-hosted options for ease of use and resource management. Using APIs allows me to avoid hardware stress and simplifies deployment.

[![OpenRouter](https://img.shields.io/badge/OpenRouter-Consolidated%20APIs-purple)](https://openrouter.ai/)
[![Google Flash 2.0](https://img.shields.io/badge/Google%20Flash%202.0-Primary%20LLM-blue)](https://developers.generativeai.google/models/gemini)
[![Qwen](https://img.shields.io/badge/Qwen-Coder-green)](https://qwen.modelscope.cn/)
[![Cohere](https://img.shields.io/badge/Cohere-Instructional-yellow)](https://cohere.com/)
[![Sonnet](https://img.shields.io/badge/Sonnet-3.7-red)](https://blog.google/technology/ai/gemini-api-developers-cloud/)

- I use **OpenRouter** to consolidate billing and access a wide variety of APIs, enabling me to select models best suited for specific tasks.

- **Google Flash 2.0** is my primary go-to model due to its fast inference, large context window, and reasonable pricing. While not the best for complex reasoning, its versatility makes it suitable as the backing model for all my Assistant configurations.

- For code generation that isn't agentic or for debugging purposes, I often turn to **Qwen's models**. I find the Qwen coder particularly underrated.

- **Cohere** is useful for instructional text-based tasks.

- While I sometimes use **OpenAI**, especially **Sonnet 3.7** for agented code generation, I've found its recent performance to be inconsistent.

### LLM Frontend

I've tested numerous AI tool frontends, and **Open Web UI** stands out as the most impressive. I share some of my configurations on [Open Web UI](https://openwebui.com/u/danielrosehill). I recommend starting with a PostgreSQL database for long-term use, rather than SQLite.

[![Open Web UI](https://img.shields.io/badge/Open%20Web%20UI-Primary-blue)](https://openwebui.com/)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=flat-square&logo=github)](https://github.com/open-webui/open-webui)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Recommended-green)](https://www.postgresql.org/)
[![Chroma DB](https://img.shields.io/badge/Chroma%20DB-Default-yellow)](https://www.trychroma.com/)
[![Milvus](https://img.shields.io/badge/Milvus-Optional-purple)](https://milvus.io/)
[![Qdrant](https://img.shields.io/badge/Qdrant-Optional-orange)](https://qdrant.tech/)

While the container defaults to Chroma DB, you can configure it to use Milvus, Qdrant, or other options. Initially, self-hosting was for experimentation, but when it became robust enough to replace commercial tools, I re-architected for long-term stability, emphasizing careful component selection from the outset.

### Speech To Text / ASR

[![Whisper AI](https://img.shields.io/badge/Whisper%20AI-Chrome%20Extension-blue)](https://chromewebstore.google.com/detail/whisperai-ai-driven-speec/klhcnkknganbneegjihbcfjoifiomhfn)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=flat-square&logo=github)](https://github.com/openai/whisper)
[![Futo Keyboard](https://img.shields.io/badge/Futo%20Keyboard-Android-green)](https://futo.org/keyboard/)

Transitioning to speech-to-text has been transformative! After unsatisfactory experiences a decade ago, **Whisper** has revolutionized reliability and made it good enough for everyday use.

I use **Whisper AI** as a Chrome extension for speech-to-text and use it for many hours per day.

For Android, the open source **Futo Keyboard** project offers promise, but it depends on local hardware.

While I recognize the use case, I prefer not to run speech-to-text or most AI models locally. On my Linux desktop, I use generative AI tools to create my own notepads for Whisper via the API.

### Vector Storage

I am developing a personal managed context data store for creating personalized AI experiences. This is a long-term project and my approach is likely to change over time. I'm using a multi-agent workflow to proactively generate contextual data. You can see some of my related projects here:

- [Agentic-Context-Development-Interview-Demo](https://github.com/danielrosehill/Agentic-Context-Development-Interview-Demo)
- [Personal-RAG-Agent-Workflow](https://github.com/danielrosehill/Personal-RAG-Agent-Workflow)
- [My-LLM-Context-Repo-Public](https://github.com/danielrosehill/My-LLM-Context-Repo-Public)
- [Personal-Context-Repo-Idea](https://github.com/danielrosehill/Personal-Context-Repo-Idea)

[![Qdrant](https://img.shields.io/badge/Qdrant-Vector%20Storage-blue)](https://qdrant.tech/)
[![Crew AI](https://img.shields.io/badge/Crew%20AI-Agent%20Systems-green)](https://www.crewai.com/)

The project involves creating markdown files based on interviews detailing aspects of my life. I've also used the inverse approach of putting non-contextual data through an LLM pipeline to isolate context data. These workflows can be implemented with complex agent systems like Crew AI or by creating assistants using system prompts.

For vector storage, I avoid OpenAI assistants to prevent vendor lock-in and instead use **Qdrant** to decouple my personal context data from other parts of the project.

### Regular Storage

Storing AI outputs more robustly doesn't require specialized solutions; regular databases suffice.

[![MongoDB](https://img.shields.io/badge/MongoDB-NoSQL-green)](https://www.mongodb.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-SQL-blue)](https://www.postgresql.org/)
[![PGVector](https://img.shields.io/badge/PGVector-Extension-purple)](https://pgvector.dev/)

**MongoDB** and **PostgreSQL** are my preferred databases. PostgreSQL is especially beneficial, as it can easily be extended with PGVector.

## Agentic, Generative & Orchestration Tools

These tools enhance and extend the capabilities of the core components, enabling more complex workflows and creative applications.

### Agents, Assistants

I've explored the field of AI agents and assistants, noting that many interesting projects lack well-developed frontends. You can explore some of my AI assistants in my [AI Assistants Library](https://agents.bydanielrosehill.com/).

[![System Prompts](https://img.shields.io/badge/System%20Prompts-600%2B-blue)](https://github.com/your-repo)
[![Open Web UI](https://img.shields.io/badge/Open%20Web%20UI-Community-green)](https://openwebui.com/)
[![Dify AI](https://img.shields.io/badge/Dify%20AI-Tested-yellow)](https://dify.ai/)

I'm a strong advocate for simple system prompt-based agents and have open-sourced over 600 system prompts since discovering AI in 2024. I currently use these in Open Web UI, sharing my library with the Open Web UI community. I've also tested Dify AI, but found it less effective with such a large agent network.

While having over 600 assistants may seem excessive, it's manageable when each assistant is highly focused on a small, distinct task. For example, I have assistants for changing the persona of text, formalizing it, informalizing it, and other common writing tasks. My current focus is on orchestration and tool usage.

### Other Generative AI

Here's a look at some other generative AI tools I've been playing with:

#### Text To Image

[![Leonardo AI](https://img.shields.io/badge/Leonardo%20AI-Primary-purple)](https://leonardo.ai/)

I use **Leonardo AI** for text-to-image generation. I appreciate the diversity of models and their configurable parameters.

#### Text To Video

[![Runway ML](https://img.shields.io/badge/Runway%20ML-Animation-orange)](https://runwayml.com/)

While I haven't explored text-to-video as extensively, I use **Runway ML** for creating animations from frames.

### Workflows / Orchestration

My main interest in AI systems lies in addressing the challenge of making this rapidly growing technology more effective and versatile through tool use, workflow management, and orchestration.

[![N8N](https://img.shields.io/badge/N8N-Orchestration-blue)](https://n8n.io/)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=flat-square&logo=github)](https://github.com/n8n-io/n8n)
[![Starter Kit](https://img.shields.io/badge/AI%20Starter%20Kit-Self%20Hosted-purple?style=flat-square)](https://github.com/n8n-io/self-hosted-ai-starter-kit)
[![Open Web UI](https://img.shields.io/badge/Open%20Web%20UI-Pipelines-green)](https://openwebui.com/)

I use **N8N** to provision and orchestrate agents. I am trying out different stack combinations, prioritizing fewer components. I also like the idea of pipelines and tools within Open Web UI to enable actions on external services. I believe that we will see stack consolidation this year.

**Langflow** provides a user-friendly interface for visually building complex workflows with language models, making it easier to prototype and experiment with different LLM configurations.

[![Langflow](https://img.shields.io/badge/Langflow-Workflows-orange)](https://www.langflow.org/)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=flat-square&logo=github)](https://github.com/langflow-ai/langflow)

### Agentic Workflows & Tools

This section covers the tools and workflows I use that leverage agentic AI principles, including my choice of IDEs and how I integrate AI with my computer usage.

#### AI IDEs

[![Windsurf](https://img.shields.io/badge/Windsurf-Primary%20IDE-blue)](https://codeium.com/windsurf)
[![Aider](https://img.shields.io/badge/Aider-Single%20Scripts-green)](https://aider.chat/)

I currently subscribe to **Windsurf**, valuing its integrated experience for agent-driven code generation, despite some recent performance issues.

I also use **Aider**, especially for single-script projects where precise context specification is advantageous.

#### Computer Use

[![OpenSUSE Linux](https://img.shields.io/badge/OpenSUSE-Linux-green)](https://www.opensuse.org/)
[![Open Interpreter](https://img.shields.io/badge/Open%20Interpreter-Terminal-blue)](https://www.openinterpreter.com/)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=flat-square&logo=github)](https://github.com/OpenInterpreter/open-interpreter)

I use **OpenSUSE Linux** as my daily desktop, which influences my choice of tools.

I've found **Open Interpreter** impressive for running LLMs directly within the terminal and see significant potential in this project. It requires careful provisioning for debugging and working on the computer, but it's worth exploring.

## Docker Implementation

This repository includes a [docker-compose.yaml](./docker-compose.yaml) file that encapsulates my AI stack. This setup allows for easy deployment and management of the various components.

**Services included:**

[![OpenWebUI](https://img.shields.io/badge/OpenWebUI-Frontend-blue)](https://github.com/your-repo)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-green)](https://github.com/your-repo)
[![Qdrant](https://img.shields.io/badge/Qdrant-Vector%20DB-purple)](https://github.com/your-repo)
[![Redis](https://img.shields.io/badge/Redis-Cache-red)](https://github.com/your-repo)
[![Langflow](https://img.shields.io/badge/Langflow-Workflows-orange)](https://github.com/your-repo)
[![Linkwarden](https://img.shields.io/badge/Linkwarden-Bookmarks-teal)](https://github.com/your-repo)
[![N8N](https://img.shields.io/badge/N8N-Automation-yellow)](https://github.com/your-repo)
[![Unstructured](https://img.shields.io/badge/Unstructured-Content%20Extraction-gray)](https://github.com/your-repo)

**Key Components:**

- **OpenWebUI**:  My primary frontend for interacting with LLMs.
- **PostgreSQL**:  The main database for storing application data.
- **Qdrant**: A vector database essential for semantic search and RAG applications.
- **Redis**: Used for caching and performance optimization.
- **Langflow**: Facilitates workflow management for language models.
- **Linkwarden**:  A bookmark and web content manager for research and reference.
- **N8N**:  My chosen workflow automation platform.
- **Unstructured**: For extracting content from a variety of file formats.

In addition to these core services, the Docker Compose configuration includes:

- **Monitoring and Backup**: Glances for system monitoring and Duplicati for backups, ensuring a robust and maintainable system.

This implementation demonstrates a practical deployment of the tools and services, including necessary environment variables, volume mounts, networking configurations, and health checks.

## APIs

I leverage specialized APIs in conjunction with LLMs to enhance specific tasks.

[![Tavily](https://img.shields.io/badge/Tavily-Search%20API-blue?style=for-the-badge&logo=search)](https://tavily.com/)
[![Sonar](https://img.shields.io/badge/Sonar-Perplexity%20API-purple?style=for-the-badge&logo=perplexity)](https://docs.perplexity.ai/home)

- **Tavily**: This search API provides relevant, up-to-date information, making it ideal for RAG applications and ensuring LLMs have access to current knowledge.
- **Sonar by Perplexity**:  Perplexity's API delivers powerful search capabilities with built-in summarization and information synthesis, particularly effective for research and gathering comprehensive information on specific topics.

These APIs complement the LLM capabilities, enabling more robust AI applications with access to real-time data.