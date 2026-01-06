🤖 SEO Ranking Agent (Google Search & Local Pack)
📌 Overview

This project is an agentic SEO automation system that checks Google Search (organic) and Local Pack rankings for a list of keywords and writes structured, factual insights back into the same Excel file.

The system combines:

📊 Deterministic data collection

🧠 Rule-based decision making

🔁 State-based orchestration

✍️ Controlled LLM reasoning

👤 Human-in-the-loop verification

The focus is accuracy, transparency, and explainability, not blind automation.

✨ Key Features

📥 Reads keywords and target pages from Excel

🔍 Fetches Google organic rankings (top 50)

📍 Fetches Local Pack rankings (top 3 + Local Finder fallback up to top 20)

🧾 Generates factual, neutral explanations using an LLM

📝 Writes results back into the same Excel file

🔁 Skips already processed rows (resume-safe execution)

🌐 Opens Google Search or Maps for manual verification (optional)

📐 Preserves Excel formatting with dynamic row height adjustment

🧠 Why This Is Agentic AI

This system behaves like an agent, not a simple script.

✅ Agent Characteristics

Step-by-step execution using a state graph

Each step has a single responsibility

Decisions are based on current state, not hardcoded logic

Human verification is triggered conditionally

LLM usage is strictly constrained (no hallucinations)

📌 Example Decisions

If organic rank ≤ 10 → open Google Search

If Local Pack rank ≤ 5 → open Google Maps

If neither condition is met → no browsing

If data already exists → skip processing

🏗️ Architecture (Simple Explanation)

The system is divided into clear logical layers:

📥 1. Input Layer

Reads keywords and target URLs from Excel

Preserves existing formatting and structure

📡 2. Data Collection Layer

Google Search rankings via SerpAPI

Local Pack data using:

Google Maps engine

Local Finder fallback (tbm=lcl)

🔁 3. Agent Orchestration Layer

Implemented using a state-based graph

Nodes include:

Organic ranking check

Local Pack ranking check

Explanation generation

✍️ 4. Reasoning Layer (LLM)

Converts numeric rankings into neutral explanations

Strict rules prevent trends, assumptions, or recommendations

🧭 5. Decision Layer

Determines whether browser verification is required

Ensures human-in-the-loop validation

💾 6. Persistence Layer

Writes results back into the same Excel file

Safe for re-runs and partial execution

📍 Local Pack Ranking Logic

Local Pack ranking uses a hybrid, realistic approach:

🗺️ Google Maps results (positions 1–3)

📋 Local Finder fallback (positions 4–20)

Matching logic:

🌐 Website domain match (strongest signal)

🏷️ Business name match (fallback)

This mirrors how Google expands results when users click “More places”.

🧰 Libraries and Tools Used

📊 pandas – reading and processing Excel data

📘 openpyxl – writing results while preserving formatting

🌐 requests – API communication

🔍 SerpAPI – Google Search, Maps, and Local Finder data

🔗 LangChain – LLM integration

🧩 LangGraph – state-based agent orchestration

🧠 OpenAI API – controlled reasoning generation

🌍 webbrowser / subprocess – browser automation

🔐 python-dotenv – environment variable management

👤 Human-in-the-Loop Design

Automation is selective, not blind.

Browsing happens only for important rankings

Google Search opens before Google Maps

🕶️ Incognito / InPrivate mode supported

🔁 Graceful fallback to normal browser if needed

This ensures transparency and trust in results.

📄 Excel Output Behavior

The input Excel file is updated with:

🔢 Organic rank

📍 Local Pack rank

🧾 Agent-generated explanation

📐 Auto-adjusted row height for readability

Previously processed rows are skipped on future runs.

📁 Why the Code Is in a Single File

The code is intentionally kept in one file to:

🔍 Make auditing and debugging easier

🧠 Show the complete agent flow clearly

🧱 Avoid premature abstraction

🎯 Keep interview discussions simple

Logical separation is handled via functions and agent nodes.
The code can be modularized later without changing behavior.

🛡️ Safety and Reliability

❌ No speculative insights

❌ No hallucinated explanations

❌ No destructive Excel operations

⏱️ API throttling protection included

🔁 Resume-safe execution

⚙️ Installation

Install dependencies:

pip install pandas openpyxl requests python-dotenv langchain langgraph

🔐 Environment Setup

Create a .env file in the project root:

SERP_API_KEY=your_serpapi_key
OPENAI_API_KEY=your_openai_key

▶️ How to Run
python main.py


The script updates the same Excel file with rankings and explanations.

🏁 Summary

This project demonstrates how agentic AI can be applied to SEO analysis by combining:

📊 Deterministic data collection

🔁 State-based orchestration

🧠 Rule-driven decisions

✍️ Controlled LLM reasoning

👤 Human verification

It prioritizes accuracy, explainability, and safety over aggressive automation.
