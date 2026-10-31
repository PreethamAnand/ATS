# 🎯 Enterprise ATS Resume Analyzer

> **An intelligent, multi-agent resume analysis system that helps candidates optimize their resumes for Applicant Tracking Systems (ATS) and land more interviews.**

Built with **LangChain**, **LangGraph**, **OpenRouter**, and **sentence-transformers**, this system reads a resume and a job description, then produces a complete, actionable report — scoring, gap analysis, and rewrite suggestions — in a single automated pipeline.

---

## ✨ What This Project Does

Upload a resume and paste a job description. Within seconds, five specialized AI agents work together to:

- 📄 **Parse and clean** your resume into ATS-friendly structured data
- 📋 **Understand the job description** — extracting required skills, responsibilities, and hidden keywords
- 🔍 **Match your resume against the job** using both keyword matching and semantic (meaning-based) similarity
- 📊 **Evaluate your experience, projects, and achievements** for relevance and impact
- 🏆 **Generate a final ATS score**, grammar check, missing-section audit, and a prioritized improvement plan — complete with bullet point rewrites

The result is a polished, easy-to-read report that tells you exactly what to fix and how to fix it.

---

## 🧠 How It Works

```
                 ┌──────────────────────────────┐
                 │   Resume (PDF/DOCX) + JD     │
                 └──────────────┬───────────────┘
                                │
                                ▼
        ┌────────────────────────────────────────────┐
        │           LangGraph Orchestrator           │
        │                                            │
        │   ① Ingestion Agent     ② JD Agent         │
        │      (runs in parallel — instant insights) │
        │                                            │
        │   ③ Matching Agent                         │
        │      → keyword + semantic + skill-gap      │
        │                                            │
        │   ④ Deep Analysis Agent                    │
        │      → experience, projects, achievements  │
        │                                            │
        │   ⑤ Scoring & Recommendation Agent         │
        │      → final ATS score + action plan       │
        └──────────────────────┬─────────────────────┘
                               │
                                ▼
                  📑 Full JSON / Visual Report
```

Each agent has a focused responsibility, and the LangGraph pipeline coordinates them seamlessly — passing structured data from one stage to the next with zero manual glue code.

---

## 🚀 Key Features

| Feature | Description |
|---|---|
| **Smart Resume Parsing** | Extracts contact info, experience, education, skills, projects, and certifications into clean structured data |
| **Deep JD Understanding** | Identifies required vs. preferred skills, seniority level, and hidden ATS keywords |
| **Dual Matching Engine** | Combines exact keyword matching with AI-powered semantic similarity for accurate scoring |
| **Skill Gap Analysis** | Highlights missing skills and surfaces transferable skills you may not have emphasized |
| **Experience & Impact Scoring** | Evaluates career progression, project quality, and quantified achievements |
| **Actionable Recommendations** | Prioritized action items, quick wins, and ready-to-use bullet point rewrites |
| **Grammar & Section Audit** | Flags missing resume sections and grammar issues automatically |
| **Interactive Dashboard** | Clean Streamlit UI with score gauges, breakdowns, and downloadable reports |

---

## 🏗️ Project Structure

```
ats_langchain/
├── agents/
│   ├── llm_factory.py           # Centralized LLM configuration
│   ├── ingestion_agent.py        # Resume parsing & ATS formatting
│   ├── jd_agent.py                # Job description analysis
│   ├── matching_agent.py          # Keyword + semantic + skill-gap matching
│   ├── deep_analysis_agent.py     # Experience, projects, achievements
│   └── scoring_agent.py           # Final scoring & recommendations
├── tools/
│   ├── file_reader.py             # PDF/DOCX text extraction
│   ├── keyword_tool.py            # Deterministic keyword matching
│   ├── semantic_tool.py           # Embedding-based similarity
│   └── grammar_tool.py            # Grammar checking
├── chains/
│   └── ats_graph.py               # LangGraph pipeline definition
├── models/
│   └── schemas.py                 # Pydantic data models
├── api/
│   └── main.py                    # FastAPI backend
├── app.py                          # Streamlit dashboard
├── tests/
│   └── test_pipeline.py
├── .env
└── requirements.txt
```

---

## ⚡ Quick Start

### 1. Set up the environment
```bash
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

pip install -r requirements.txt
python -m spacy download en_core_web_lg
```

### 2. Configure your API keys
```bash
cp .env.example .env
```
Then fill in:
```env
OPENROUTER_API_KEY=your_key_here
LLM_MODEL=google/gemini-2.5-flash
EMBEDDING_MODEL=all-MiniLM-L6-v2
```

### 3. Run the backend
```bash
uvicorn api.main:app --reload --port 8000
```

### 4. Run the dashboard
In a second terminal:
```bash
streamlit run app.py
```

Open your browser at `http://localhost:8501`, upload a resume, paste a job description, and click **Analyze Resume** 🎯

---

## 🛠️ Tech Stack

- **LangChain** — LLM orchestration and structured output parsing
- **LangGraph** — Multi-agent pipeline coordination with shared state
- **OpenRouter** — Flexible access to LLMs (Gemini, GPT, Claude, and more)
- **sentence-transformers** — Local embedding-based semantic matching
- **FastAPI** — Backend API
- **Streamlit + Plotly** — Interactive visual dashboard

---

## 📈 Sample Output

The final report includes:
- ✅ Overall ATS Score (0–100) with letter grade
- 📊 Category-wise score breakdown (keywords, semantics, experience, grammar, etc.)
- 🔑 Missing keywords & skills to add
- ✏️ Before/after bullet point rewrites
- ⚡ Quick wins you can apply in under 15 minutes
- 📋 Executive summary with top strengths and weaknesses

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to open a pull request or start a discussion.

---

## 📄 License

This project is open source and available under the MIT License.
