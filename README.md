# AgenticAI

## Multi-Agent Content Writer — LangGraph Assignment

This project implements a multi-agent content assistant using LangGraph. The system routes user requests to the right specialized agent and supports tool-calling loops and conversation memory.

## Problem Statement

Build a multi-agent system using LangGraph that acts as a smart content assistant.

The system includes:

1. **SEO Blog Writer**
   Writes long-form SEO blog posts and uses research/search tools.

2. **X/Twitter Writer**
   Writes short X/Twitter posts under 280 characters and uses trend/search tools.

3. **General Handler**
   Handles greetings, general questions, and memory-based follow-up questions.

## Architecture

```text
                 ┌→ SEO Blog Writer ↔ tools
User → Router ───┼→ X/Twitter Writer ↔ tools
                 └→ General Handler → END
```

## Features

* Router-based agent selection
* SEO Blog Writer agent
* X/Twitter Writer agent
* General Handler agent
* Tool-calling loop
* Conversation persistence using LangGraph checkpointer
* Google Colab compatible implementation
* OpenAI API key loaded securely from Colab Secrets
* Optional Tavily API support for real internet search
* Mock fallback data when Tavily API key is not available

## Tech Stack

* Python
* LangGraph
* LangChain
* OpenAI
* Google Colab
* Tavily Search API — optional

## Repository Structure

```text
AgenticAI/
  assignments/
    Assignment_Template_Multi_Agents_Systems.ipynb
  README.md
  requirements.txt
  .gitignore
```

## Setup Instructions

Install required dependencies:

```bash
pip install -r requirements.txt
```

For Google Colab, install dependencies using:

```python
!pip install -q -U langgraph langchain langchain-openai langchain-core tavily-python python-dotenv pydantic
```

## API Key Setup in Google Colab

Store the OpenAI key in Colab Secrets with this name:

```text
OPENAI_API_KEY
```

Use this code in the notebook:

```python
import os
from google.colab import userdata

os.environ["OPENAI_API_KEY"] = userdata.get("OPENAI_API_KEY")

if not os.environ["OPENAI_API_KEY"]:
    raise ValueError("OPENAI_API_KEY not found. Add it in Colab Secrets and enable Notebook access.")

print("OpenAI key loaded from Colab Secrets.")
```

Optional Tavily key:

```text
TAVILY_API_KEY
```

## How to Run

Open the notebook in Google Colab and run the cells in order:

1. Install dependencies
2. Load API keys
3. Define state
4. Define tools
5. Define SEO Blog Writer
6. Define X/Twitter Writer
7. Define General Handler
8. Define Router
9. Build LangGraph workflow
10. Run test prompts

## Sample Test Prompts

```python
run_content_assistant(
    "Write an SEO blog on how AI agents can improve CRM applications.",
    thread_id="assignment-test-thread-001"
)
```

```python
run_content_assistant(
    "Write 3 tweets about AI agents in sales operations.",
    thread_id="assignment-test-thread-001"
)
```

```python
run_content_assistant(
    "What was my last request?",
    thread_id="assignment-test-thread-001"
)
```

## Assignment Requirements Mapping

| Requirement       | Implementation                                             |
| ----------------- | ---------------------------------------------------------- |
| Router            | Routes request to SEO, X/Twitter, or General Handler       |
| SEO Blog Writer   | Generates long-form SEO content                            |
| X/Twitter Writer  | Generates posts under 280 characters                       |
| General Handler   | Handles general questions and memory-based follow-ups      |
| Tool-calling loop | Agents call tools, receive results, and continue or finish |
| Persistence       | LangGraph checkpointer stores conversation state           |
| Memory test       | Same `thread_id` supports follow-up memory questions       |

## Notes

Do not commit API keys or secrets to GitHub. API keys should be stored only in Google Colab Secrets or local environment variables.

## Author

Naga Mantha
