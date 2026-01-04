SEO Ranking Agent (Google Search & Maps)

This project is an agentic SEO automation system that checks Google Search and Maps rankings for a list of keywords and writes structured insights back into the same Excel file.

It combines deterministic data collection, rule-based decision making, and LLM-powered reasoning, while keeping a human-in-the-loop for verification.

What This Project Does

Reads keywords and target pages from an Excel sheet

Checks:

Google organic search rankings (top 50)

Google Maps rankings (top 20)

Generates neutral, factual explanations using an LLM

Automatically opens Google Search and/or Maps for manual verification when required

Writes all results back into the same Excel file

Supports resume-safe execution (already processed rows are skipped)

Why This Is Agentic AI

This system goes beyond basic automation and behaves like an agent:

It operates in clearly defined steps

Each step has a single responsibility

Decisions are made based on state and rules

Human verification is triggered only when needed

Example behavior:

If organic rank is within the top 10, Google Search is opened

If Maps rank is within the top 5, Google Maps is opened

If neither condition is met, no browsing occurs

Explanations are generated strictly from collected data

Architecture (Simple Explanation)

The architecture is divided into clear layers:

Input Layer
Reads keywords from Excel while preserving formatting.

Data Collection Layer
Fetches Google Search and Google Maps rankings using SerpAPI.

Agent Orchestration Layer
Uses a state-based agent graph where each node performs a single task:

Organic ranking

Maps ranking

Reasoning

Reasoning Layer (LLM)
Converts numeric results into neutral explanations under strict constraints.

Decision Layer
Determines whether human verification is required and conditionally opens Google Search or Maps.

Persistence Layer
Writes results back into the same Excel file and allows safe resumption on future runs.

Technologies and Libraries Used
Tool / Library	Purpose
pandas	Reading and processing Excel data
openpyxl	Writing results back into Excel while preserving formatting
requests	Making API calls
SerpAPI	Fetching Google Search and Maps results
LangChain	Integrating the LLM
LangGraph	Orchestrating agent state and execution flow
OpenAI API	Generating factual, constrained explanations
webbrowser / subprocess	Opening Google Search and Maps for verification
python-dotenv	Secure environment variable management
Why the Code Is in a Single File

This is a deliberate design choice:

The script is audit-heavy and manually reviewed

Keeping logic in one file simplifies debugging and verification

Logical separation exists through functions and agent nodes

The code can be modularized later without changing core logic

This prioritizes clarity and control over premature abstraction.

Human-in-the-Loop Design

The system does not blindly automate actions.

Browsing is triggered only for important results

Google Search opens before Google Maps

Incognito or InPrivate mode is supported for Chrome and Edge

A graceful fallback is used if incognito is unavailable

This ensures transparency and trust in the output.

Excel Output

The same input file is updated with:

Google Search rank

Google Maps rank

Agent-generated explanation

Automatically adjusted row height for readability

Previously processed rows are skipped on subsequent runs.

Safety and Reliability

No trend assumptions or speculative insights

No hallucinated explanations

No destructive Excel operations

API throttling safeguards included

Resume-safe execution

How to Run

Install dependencies:

pip install pandas openpyxl requests python-dotenv langchain langgraph


Create a .env file:

SERP_API_KEY=your_serpapi_key
OPENAI_API_KEY=your_openai_key


Run the script:

python main.py

Final Notes

This project demonstrates:

Agentic system design

Responsible use of large language models

Rule-based decision making

Human-in-the-loop verification

Practical SEO automation

It is designed for clarity, control, and trust rather than blind automation.

