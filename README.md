# AI Agents (LangGraph + LangChain)

This project demonstrates a multi-agent operations intelligence system built with **LangGraph and LangChain**.

The system integrates multiple data sources and tools to support dispatch and operations decision-making.

Original project inspiration:  
[<original repo link>](https://github.com/RohanMathur/MSBA_AI_Agents_Demo#)

I cloned this project to study the architecture of **multi-agent workflows, RAG pipelines, and tool integration**, and I plan to extend it with additional features and improvements.

---

## System Overview

This multi-agent system performs the following tasks:

- Reads business context and KPI definitions from a **dispatch playbook PDF (RAG)**
- Analyzes operational data from **CSV files** (KPI computation + anomaly detection)
- Retrieves **weather forecasts** and derives dispatch risk
- Uses planning agents to generate **dispatch recommendations**
- Produces a **leadership-ready HTML report**
- Optionally emails the report via **Gmail SMTP**

---

## Architecture

High-level pipeline:

PDF Playbook → RAG Knowledge Base  
CSV Data → KPI + Anomaly Analysis  
Weather API → Route Risk Evaluation  
Planner Agent → Dispatch Plan  
Report Agent → HTML Report  
Email Tool → Stakeholder Delivery

The system is orchestrated using **LangGraph**, where each node represents a processing step in the workflow.

---

## Project Structure
data/ input PDF + CSV files
src/ application code
chroma_db/ local vector database (not committed)
.env environment variables (not committed)

---

## Setup

```bash
python3.11 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

cp .env.example .env
```

Fill in:
- OPENAI_API_KEY=
- REPORT_EMAIL_TO=
- GMAIL_APP_PASSWORD=

---

## Run the system

```bash
python src/main.py
```

The pipeline will:

1. Load the PDF playbook and build a vector database
2. Analyze the shipment CSV
3. Retrieve weather conditions along the route
4. Generate a dispatch plan
5. Produce an HTML report
6. Optionally send the report via email

---

## Future Improvements

Planned improvements include:

- caching the vector database to avoid rebuilding embeddings
- improving anomaly detection for operational metrics
- adding evaluation metrics for agent decisions
- supporting additional data sources (databases / APIs)
- improving planner agent reasoning
