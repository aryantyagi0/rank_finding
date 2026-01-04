SEO Ranking Agent (Google Search & Maps)

This project is an agentic SEO automation system that checks Google Search and Maps rankings for a list of keywords and writes structured insights back into the same Excel file.

It combines deterministic data collection, rule-based decision making, and controlled LLM reasoning while keeping a human-in-the-loop for verification.

What the Project Does

Reads keywords and target pages from an Excel file

Fetches Google organic search rankings (top 50 results)

Fetches Google Maps rankings (top 20 results)

Generates factual, neutral explanations using an LLM

Opens Google Search or Maps for manual verification when needed

Writes all results back into the same Excel file

Skips already processed rows for safe re-runs

Why This Is Agentic AI

This system behaves like an agent rather than a simple script.

It works in clearly defined steps

Each step has a single responsibility

Decisions are made based on state and rules

Human verification is triggered conditionally

Examples:

If organic rank is in the top 10, Google Search is opened

If Maps rank is in the top 5, Google Maps is opened

If neither condition is met, no browsing occurs

The LLM never invents data or recommendations

Architecture (Simple Explanation)

The architecture is divided into logical layers:

Input Layer
Reads keywords from Excel while preserving formatting.

Data Collection Layer
Fetches Google Search and Maps rankings using SerpAPI.

Agent Orchestration Layer
Uses a state-based graph where each node performs one task:

Organic ranking check

Maps ranking check

Reasoning generation

Reasoning Layer (LLM)
Converts numeric results into neutral explanations under strict rules.

Decision Layer
Decides whether Google Search or Maps should be opened for verification.

Persistence Layer
Writes results back into the same Excel file and supports resume-safe runs.

Libraries and Tools Used

pandas – reading and processing Excel data

openpyxl – writing results back while preserving Excel formatting

requests – API communication

SerpAPI – Google Search and Google Maps data

LangChain – LLM integration

LangGraph – state-based agent orchestration

OpenAI API – controlled reasoning generation

webbrowser / subprocess – browser automation for verification

python-dotenv – environment variable management

Human-in-the-Loop Design

The system does not blindly automate actions.

Browsing happens only for important keywords

Google Search opens before Google Maps

Incognito/InPrivate mode is supported for Chrome and Edge

Graceful fallback to normal browser if incognito is unavailable

This keeps the process transparent and verifiable.

Excel Output Behavior

The same input file is updated with:

Google Search rank

Google Maps rank

Agent-generated explanation

Automatically adjusted row height for long text

Previously processed rows are skipped on future runs.

Why the Code Is in a Single File

The code is intentionally kept in one file:

Easier auditing and debugging

Clear visibility of agent flow

Logical separation is handled via functions and agent nodes

Can be modularized later without changing behavior

This prioritizes clarity over premature abstraction.

Safety and Reliability

No speculative insights or trends

No hallucinated explanations

No destructive Excel operations

API throttling protection included

Resume-safe execution

How to Run

Install dependencies:

pip install pandas openpyxl requests python-dotenv langchain langgraph


Create a .env file:

SERP_API_KEY=your_serpapi_key
OPENAI_API_KEY=your_openai_key


Run the script:

python main.py
