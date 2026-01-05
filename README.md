SEO Ranking Agent (Google Search & Maps)
Overview

This project is an agentic SEO automation system that checks Google Search and Google Maps / Local rankings for a list of keywords and writes structured, factual insights back into the same Excel file.

It combines:

Deterministic data collection

Rule-based decision making

Controlled LLM reasoning

Human-in-the-loop verification

The system is designed to be transparent, resume-safe, and non-speculative.

What the Project Does

Reads keywords and target pages from an Excel file

Fetches Google organic search rankings (top 50 results)

Fetches Google local rankings (Local Pack + extended places up to top 20)

Generates factual, neutral explanations using an LLM

Opens Google Search or Maps only when verification is needed

Writes all results back into the same Excel file

Skips already processed rows for safe re-runs

Why This Is Agentic AI

This system behaves like an agent, not a simple script.

Key agent characteristics:

Clear step-by-step execution

Each step has a single responsibility

Decisions are made based on state and rules

Human verification is triggered conditionally

The LLM is constrained and non-creative

Example decision rules:

If organic rank ≤ 10 → Google Search may open

If local rank ≤ 5 → Google Maps may open

If neither condition is met → no browsing occurs

The LLM never invents data, trends, or recommendations

Architecture (Simple Explanation)

The architecture is divided into logical layers:

1. Input Layer

Reads keywords from Excel

Preserves formatting and structure

2. Data Collection Layer

Fetches Google Search results using SerpAPI

Fetches Local Pack and extended local places

Uses strict matching rules (domain + business name)

3. Agent Orchestration Layer

Implemented using a state-based graph

Each node performs exactly one task:

Organic ranking check

Local ranking check

Explanation generation

4. Reasoning Layer (LLM)

Converts numeric results into neutral explanations

Operates under strict rules:

No assumptions

No trends

No recommendations

No hallucinations

5. Decision Layer

Decides whether browsing is required

Controls Search vs Maps priority

Supports incognito / private browsing

6. Persistence Layer

Writes results back into the same Excel file

Automatically adjusts row height

Skips completed rows on re-runs

Libraries and Tools Used

pandas
Reading and processing Excel data

openpyxl
Writing results back while preserving Excel formatting

requests
API communication

SerpAPI
Google Search, Local Pack, and Google Maps data

LangChain
Controlled LLM integration

LangGraph
State-based agent orchestration

OpenAI API
Deterministic reasoning generation

webbrowser / subprocess
Browser automation for manual verification

python-dotenv
Environment variable management

Human-in-the-Loop Design

The system does not blindly automate decisions.

Browsing happens only for important cases

Google Search opens before Google Maps

Incognito / InPrivate mode supported (Chrome & Edge)

Graceful fallback to normal browser if incognito is unavailable

This ensures auditability and trust.

Excel Output Behavior

The same input file is updated with:

Google Search rank

Local (Pack + extended places) rank

Agent-generated explanation

Additional behaviors:

Row height auto-adjusts for long explanations

Formatting is preserved

Previously processed rows are skipped safely

Why the Code Is in a Single File

The code is intentionally kept in one file.

Reasons:

Easier auditing and debugging

Clear visibility of the full agent flow

No hidden execution paths

Logical separation handled via functions and agent nodes

The code can be modularized later without changing behavior.
Clarity is prioritized over premature abstraction.

Safety and Reliability

No speculative insights

No hallucinated explanations

No destructive Excel operations

API rate-limit protection included

Resume-safe execution

How to Run
1. Install dependencies
pip install pandas openpyxl requests python-dotenv langchain langgraph

2. Create a .env file
SERP_API_KEY=your_serpapi_key
OPENAI_API_KEY=your_openai_key

3. Run the script
python main.py

Summary

This project demonstrates:

Practical agentic AI design

Deterministic + LLM hybrid architecture

Human-in-the-loop automation

Production-safe Excel processing

Explainable and auditable SEO analysis

It is built for clarity, control, and correctness, not blind automation.
