# CRM Lead Qualifier Agent

## Overview

This project implements a CRM Lead Qualifier Agent that evaluates inbound leads and recommends the next best action for Sales or Marketing teams.

The agent is designed to support CRM and GTM workflows by helping teams classify, prioritize, and route leads based on lead quality, business context, and engagement signals.

## Objective

The goal of this project is to demonstrate how an AI agent can assist with lead qualification by analyzing lead information and producing a structured qualification decision.

The agent can help answer questions such as:

* Is this lead qualified?
* What is the lead priority?
* Should the lead be routed to Sales, Marketing, or nurture?
* What is the recommended follow-up action?
* What reasoning supports the qualification decision?

## Key Features

* CRM lead qualification
* Lead scoring support
* Qualification reasoning
* Recommended next best action
* Sales-ready summary generation
* Agent-based workflow
* Google Colab compatible implementation
* Secure API key usage through Colab Secrets

## Example Use Cases

* Qualify inbound website leads
* Prioritize MQLs for Sales follow-up
* Identify leads that should stay in nurture
* Generate sales handoff summaries
* Support Marketing Operations and RevOps lead review

## Architecture

```text
User / CRM Lead Data
        ↓
CRM Lead Qualifier Agent
        ↓
Lead Analysis
        ↓
Qualification Decision
        ↓
Recommended Action
```

## Sample Input

```json
{
  "first_name": "John",
  "last_name": "Smith",
  "company": "Acme Corp",
  "title": "VP of Sales Operations",
  "email": "john.smith@acme.com",
  "company_size": "1000+",
  "industry": "Technology",
  "lead_source": "Webinar",
  "engagement": "Attended demo webinar and downloaded whitepaper"
}
```

## Sample Output

```json
{
  "qualification_status": "Qualified",
  "priority": "High",
  "recommended_owner": "Sales",
  "next_best_action": "Assign to SDR for follow-up within 24 hours",
  "reasoning": "The lead has strong buying intent, senior title, relevant industry, and recent engagement with high-value marketing assets."
}
```

## Tech Stack

* Python
* LangChain / LangGraph
* OpenAI
* Google Colab
* GitHub

## Repository Structure

```text
AgenticAI/
  CRM_Lead_Qualifier_Agent_solution.ipynb
  README.md
  requirements.txt
  .gitignore
```

## Setup Instructions

Install dependencies:

```bash
pip install -r requirements.txt
```

For Google Colab:

```python
!pip install -q -U langchain langchain-openai langgraph python-dotenv pydantic
```

## API Key Setup in Google Colab

Store the OpenAI API key in Colab Secrets using this name:

```text
OPENAI_API_KEY
```

Then load it in the notebook:

```python
import os
from google.colab import userdata

os.environ["OPENAI_API_KEY"] = userdata.get("OPENAI_API_KEY")

if not os.environ["OPENAI_API_KEY"]:
    raise ValueError("OPENAI_API_KEY not found. Add it in Colab Secrets and enable Notebook access.")

print("OpenAI key loaded from Colab Secrets.")
```

## How to Run

Open the notebook in Google Colab and run the cells in order:

1. Install dependencies
2. Load API key
3. Define lead input data
4. Define agent prompt or workflow
5. Run the CRM Lead Qualifier Agent
6. Review qualification output
7. Test with multiple lead examples

## Assignment / Project Outcome

This project demonstrates how AI agents can support CRM and GTM operations by improving lead qualification consistency, reducing manual review effort, and helping Sales teams focus on higher-priority leads.

## Notes

Do not commit API keys, secrets, or `.env` files to GitHub. Keep all credentials in Google Colab Secrets or local environment variables.

## Author

Naga Mantha
