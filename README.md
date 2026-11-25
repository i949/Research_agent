# Research Agent

A source-grounded research agent built with LangChain, LangGraph, and Groq. The complete Python project is in [research-agent.zip](research-agent.zip); the Colab quickstart is [research_agent_colab.ipynb](research_agent_colab.ipynb).

## Models

Set GROQ_MODEL to choose one of the supported Groq tool-calling models:

- openai/gpt-oss-120b (default)
- openai/gpt-oss-20b
- llama-3.3-70b-versatile

## Tools

1. Web search with Tavily, with automatic parameter selection and deduplicated results.
2. ArXiv search for academic papers.
3. Wikipedia search for background material.
4. read_webpage, which reads a supplied public URL and does not search.

The agent is instructed to prefer primary sources, inspect pages before citing them, separate event dates from publication dates, and disclose unsupported or conflicting evidence.

## Run locally

Use Python 3.10 or newer. Install dependencies and the project, then set your own API keys in a local .env file copied from .env.example:

    python -m pip install -r requirements.txt
    python -m pip install -e .
    python -m research_agent "What are recent advances in quantum error correction?"

Required keys: GROQ_API_KEY and TAVILY_API_KEY. Never commit .env or put API keys in code.

## Run in Colab

Open research_agent_colab.ipynb, add GROQ_API_KEY and TAVILY_API_KEY to Colab Secrets, and run the cells. When prompted, upload research-agent.zip from this repository.

The URL reader only fetches public HTTP(S) pages and has size and redirect limits. Important claims and citations should still be reviewed.
