# My AI Stack

![alt text](banner.webp)

![Last Updated](https://img.shields.io/badge/Last%20Updated-March%2014%2C%202025-blue)
![Status](https://img.shields.io/badge/Status-Evolving-brightgreen) 
![Focus](https://img.shields.io/badge/Focus-Productivity-orange)
![Docker](https://img.shields.io/badge/Docker-Compose-blue)

## Table of Contents

- [My AI Stack](#my-ai-stack)
  - [Table of Contents](#table-of-contents)
  - [Docker Implementation](#docker-implementation)
  - [LLM APIs](#llm-apis)
  - [AI IDEs](#ai-ides)
  - [Text To Image](#text-to-image)
  - [Text To Video](#text-to-video)
  - [Speech To Text / ASR](#speech-to-text--asr)
  - [Vector Storage](#vector-storage)
  - [Regular Storage](#regular-storage)
  - [Browser Use](#browser-use)
  - [Computer Use](#computer-use)
  - [LLM Frontend](#llm-frontend)
  - [Agents, Assistants](#agents-assistants)
  - [Workflows / Orchestration](#workflows--orchestration)

This repository documents my current AI stack and tools that I use regularly. Given the rapid pace of development in AI, my stack is always evolving, but these are the components that I really like to date.

## Docker Implementation

This repository includes a [docker-compose.yaml](./docker-compose.yaml) file that implements my actual AI stack. The Docker Compose setup includes the following services:

![OpenWebUI](https://img.shields.io/badge/OpenWebUI-Frontend-blue)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-green)
![Qdrant](https://img.shields.io/badge/Qdrant-Vector%20DB-purple)
![Redis](https://img.shields.io/badge/Redis-Cache-red)
![Langflow](https://img.shields.io/badge/Langflow-Workflows-orange)
![Linkwarden](https://img.shields.io/badge/Linkwarden-Bookmarks-teal)
![N8N](https://img.shields.io/badge/N8N-Automation-yellow)
![Unstructured](https://img.shields.io/badge/Unstructured-Content%20Extraction-gray)

The Docker Compose configuration includes:

- **OpenWebUI**: Frontend for interacting with LLMs
- **PostgreSQL**: Database for storing application data
- **Qdrant**: Vector database for semantic search and RAG
- **Redis**: Caching and performance optimization
- **Langflow**: Workflow management for language models
- **Linkwarden**: Bookmark and web content manager
- **N8N**: Workflow automation platform
- **Unstructured**: Content extraction for various file formats
- **Monitoring and Backup**: Glances for system monitoring and Duplicati for backups

This implementation represents the practical deployment of the tools and services described in this document. The configuration includes environment variables, volume mounts, networking, and health checks to ensure a robust and maintainable system.

## LLM APIs

![OpenRouter](https://img.shields.io/badge/OpenRouter-Consolidated%20APIs-purple)
![Google Flash 2.0](https://img.shields.io/badge/Google%20Flash%202.0-Primary%20LLM-blue)
![Qwen](https://img.shields.io/badge/Qwen-Coder-green)
![Cohere](https://img.shields.io/badge/Cohere-Instructional-yellow)
![Sonnet](https://img.shields.io/badge/Sonnet-3.7-red)

I'm a big fan of using large language models via API. Although I have self-hosted and found uses for a few local large language models in day-to-day use, I much prefer to use them via the API where I don't have to worry about my hardware being under stress or it's just easier.

I use Open Router to consolidate billing and to give me access to a wide variety of different APIs. I tend to use different models for different tasks.

At the time of writing, Google Flash 2.0 is actually my go-to day-to-day model. I find the inference fast. I find its large context window often very useful, and its pricing is very reasonable as well. It's not the best model for reasoning or general purpose, but it's good enough for most use cases and I like its versatility, so I use it as the backing model for all my Assistant configurations.

For cogeneration that is not agentic or debugging, I'll sometimes use Qwen's models, which I'm very fond of. I think the Qwen coder is one of the most underrated LLMs currently.

I find Cohere particularly useful for instructional text-based tasks. I actually use OpenAI quite irregularly. And for agented code generation I use Sonnet 3.7. However, like many, I'm finding that its performance lately is not that wonderful and I'm sometimes reverting to 3.5.

## AI IDEs

![Windsurf](https://img.shields.io/badge/Windsurf-Primary%20IDE-blue)
![Aider](https://img.shields.io/badge/Aider-Single%20Scripts-green)

Currently I subscribe to Windsurf, although like many I have found its performance lately very poor. But it does provide a useful and integrated experience for agent to code generation.

I like Aider as well and try to use it in projects like single scripts where being able to specify exactly which context to provide is advantageous.

## Text To Image

![Leonardo AI](https://img.shields.io/badge/Leonardo%20AI-Primary-purple)

For text to image I like using Leonardo AI. I really appreciate the diversity of models and their parameters that it allows and find it very helpful.

## Text To Video

![Runway ML](https://img.shields.io/badge/Runway%20ML-Animation-orange)

I haven't explored text to video as much as other generative AI tools, but for the interesting use case of taking frames and making animation I use Runway ML.

## Speech To Text / ASR

![Whisper AI](https://img.shields.io/badge/Whisper%20AI-Chrome%20Extension-blue)
![Futo Keyboard](https://img.shields.io/badge/Futo%20Keyboard-Android-green)

One of the most transformative uses for AI that I found has been moving from typing to speech to text as my daily interface for using computer devices. The last time I tried seriously using speech to text was probably 10 years ago and the technology was fairly terrible. It remains imperfect, but Whisper has brought about a transformation in quality and has taken its reliability from being lackluster to good enough for everyday use.

I use Whisper AI which is a Chrome extension for speech to text, and reckon that I probably use it many hours per day. For Android it's a little trickier to find at the moment. There is an interesting project called Futo Keyboard, but it's local Whisper so it relies upon you having good enough hardware.

While I understand the use case overall, I am not a big fan of running speech to text or most AI models locally for that matter. On the Linux desktop I used generative AI tools to create my own notepads for using Whisper via the API.

## Vector Storage

![Qdrant](https://img.shields.io/badge/Qdrant-Vector%20Storage-blue)
![Crew AI](https://img.shields.io/badge/Crew%20AI-Agent%20Systems-green)

I'm working on a long-term project of creating a personal managed context data store in order to easily create personalized AI experiences. This is a long-term project and my approach is likely to change over time. But currently I'm using a multi-agent workflow to proactively generate contextual data for exactly this purpose. Some notes are on Github, but my approach to this is always changing.

At the moment the project consists of creating markdown files based on these interviews describing details of my life. I've also used a reverse approach of taking non-contextual data and putting it through an LLM pipeline in order to isolate the context data. These workflows can be achieved either with more complex agent systems like Crew AI or by simply creating assistants using system prompts.

Either way, you're going to eventually need some form of vector storage to hold the data. I've avoided using OpenAI assistants for the reason that doing this would tie my project to OpenAI. In order to allow my personal context door to be decoupled from other parts of the project, I use Qdrant for storing context data.

## Regular Storage

![MongoDB](https://img.shields.io/badge/MongoDB-NoSQL-green)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-SQL-blue)
![PGVector](https://img.shields.io/badge/PGVector-Extension-purple)

A lot of my early exploration of AI tools was considering how to store AI outputs more robustly. This wasn't really requiring anything special, unlike storing these for semantic retrieval, you can just use regular databases. MongoDB and PostgreSQL are my favorite tools to use. There's a lot to be said for using PostgreSQL as it's easy to then extend that to include a PGVector.

## Browser Use

![Browser Use](https://img.shields.io/badge/Browser%20Use-Independent%20Web-orange)

One of the most interesting AI projects that I've come across recently is Browser Use which provides for independent use of a web browser. I've created a basic GUI front end for easily spinning up tasks using it, and this is one of the most powerful and potentially interesting use cases for Eject AI.

## Computer Use

![OpenSUSE Linux](https://img.shields.io/badge/OpenSUSE-Linux-green)
![Open Interpreter](https://img.shields.io/badge/Open%20Interpreter-Terminal-blue)

I use OpenSUSE Linux as my daily desktop, so my choice of tools is a little bit different than what a lot of people might go for, but I have used Open Interpreter for actually running an LLM directly within the terminal and it's been very impressive. I see lots of potential in this tool. It does require closer provision for debugging and working on your computer, but it's a project that's very worth exploring.

## LLM Frontend

![Open Web UI](https://img.shields.io/badge/Open%20Web%20UI-Primary-blue)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Recommended-green)
![Chroma DB](https://img.shields.io/badge/Chroma%20DB-Default-yellow)
![Milvus](https://img.shields.io/badge/Milvus-Optional-purple)
![Qdrant](https://img.shields.io/badge/Qdrant-Optional-orange)

I've tried out most of the front ends for AI tools. So far Open Web UI has impressed me the most, although I advise those looking to use it long term to start with the PostgreSQL database rather than SQLite. While the container provides Chroma DB by default, you can change that to use Milvus, Qdrant and a couple of other options. When I was playing around with the idea of self-hosting my own LLM front end, I wasn't really thinking about it for the long term. When it became good and stable enough to use in place of commercial tools, I decided to rearchitect. Of course, it's easier to do this at the start of the project and choose your components carefully.

## Agents, Assistants

![System Prompts](https://img.shields.io/badge/System%20Prompts-600%2B-blue)
![Open Web UI](https://img.shields.io/badge/Open%20Web%20UI-Community-green)
![Dify AI](https://img.shields.io/badge/Dify%20AI-Tested-yellow)

It's taken me a little while to explore the realm of AI agents and assistants. There are a lot of interesting projects out there at the moment, but not so many of them have well-developed front ends.

I'm a huge user and exponent of simple system prompt-based agents and since discovering AI in 2024 I've created an open source to more than 600 system prompts. Currently I use these in Open Web UI and my library of these is shared with Open Web UI community. I've tried using Dify AI as well, but I found that it didn't really work well with such a big agent network.

While it might seem strange or extraordinary to have created more than 600 assistants just for my own use, it's actually not that many. Not that difficult to do with such a number, if you're following the recommendation of keeping each one very distinct and focused on a small task. For example, I have different assistants for changing the person in text, formalizing text, making text more informal, and other common writing use agents. Therefore, it's not that hard to come up with a big network. And my challenge and thought now is figuring out things like orchestration.

## Workflows / Orchestration

![N8N](https://img.shields.io/badge/N8N-Orchestration-blue)
![Open Web UI](https://img.shields.io/badge/Open%20Web%20UI-Pipelines-green)

Currently my main interest in AI systems is in figuring out the challenge, like many of how to make this vastly growing and maturing technology work and do more things, this involves looking into things like tool use, workflow management, orchestration. I like using N8N to play around with provisioning agents and orchestrating them. Right now I'm less tied into any one platform and I'm more trying out different combinations of stacks in order to make it all work. Personally, the less components of a stack the better. I like the idea very much of using pipelines and tools with Open Web UI, in order to get the existing configurations I have to actually take action on external services. I think that as much as we will see a lot of tools coming online this year, we'll also see a lot of stack consolidation and rationalization.
