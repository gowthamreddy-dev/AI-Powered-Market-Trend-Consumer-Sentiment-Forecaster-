# 🧠 AI-Powered Market Trend & Consumer Sentiment Forecaster

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![Streamlit](https://img.shields.io/badge/Streamlit-Live-red?style=flat-square&logo=streamlit)
![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-yellow?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-RAG-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-purple?style=flat-square)

> An end-to-end AI platform that aggregates consumer reviews, runs LLM-powered sentiment analysis, extracts emerging topics, and delivers real-time insights through an interactive dashboard — with role-based login, alerts, and downloadable reports.

🌐 **Live Demo:** [www.aipoweredmarkettrendandconsumersentimentforecaster.streamlit.app](https://www.aipoweredmarkettrendandconsumersentimentforecaster.streamlit.app)

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [How to Run](#-how-to-run)
- [User Roles](#-user-roles)
- [Modules](#-modules)
- [Dataset](#-dataset)
- [Milestones](#-milestones)
- [Key Results](#-key-results)
- [License](#-license)

---

## 🎯 Project Overview

This platform was built as part of an internship project to demonstrate how AI and NLP can extract actionable consumer intelligence from raw review data.

It processes **568,454 Amazon Fine Food Reviews**, runs **DistilBERT sentiment analysis** on a 5,000-review sample, extracts **8 consumer topics** using BERTopic, and answers natural language questions using a **RAG pipeline** powered by LangChain + FAISS + Groq LLaMA.

---

## ✨ Features

- 🔐 **Role-based Login** — Admin, Analyst, Marketing, Intern with different access levels
- 📊 **Interactive Dashboard** — 5 tabs with live Plotly charts and filters
- 🤖 **AI Sentiment Analysis** — DistilBERT with 97% average confidence
- 🏷️ **Topic Modeling** — BERTopic extracts emerging consumer themes
- 🔍 **RAG Pipeline** — Ask questions about reviews using LangChain + FAISS + Groq
- 🚨 **Live Alerts** — Auto-detect sentiment spikes and drops
- 📥 **Report Downloads** — One-click Excel (4 sheets) and PDF reports
- ☁️ **Word Clouds** — Visual breakdown of positive and negative language
- 📅 **Year Range Filter** — Explore trends from 2004 to 2012

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | Streamlit, Plotly, WordCloud, Matplotlib |
| **AI / NLP** | HuggingFace Transformers (DistilBERT), BERTopic |
| **RAG Pipeline** | LangChain, FAISS, Sentence Transformers |
| **LLM** | Groq API — `llama-3.3-70b-versatile` |
| **Reports** | fpdf2 (PDF), openpyxl (Excel) |
| **Data** | Pandas, NumPy |
| **Deployment** | Streamlit Community Cloud + GitHub |

---

## 📁 Project Structure

```
AI-Powered-Market-Trend-Consumer-Sentiment-Forecaster/
│
├── week6_integrated_app.py      # Main app — Login + All 5 tabs
├── Week1_data_pipeline.py       # Data scraping, cleaning, normalization
├── Week2_sentiment_topics.py    # DistilBERT sentiment + BERTopic modeling
├── Week3_rag_pipeline.py        # LangChain + FAISS + Groq RAG pipeline
├── week4_dashboard.py           # Streamlit dashboard (standalone)
├── week5_alerts_reports.py      # Alert detection + PDF/Excel reports
│
├── sentiment_results.csv        # AI sentiment scores (5,000 reviews)
├── topics_summary.csv           # BERTopic discovered topics
├── rag_insights.csv             # RAG Q&A results
├── alerts_log.csv               # Generated alerts log
│
├── faiss_index/                 # FAISS vector database
│   ├── index.faiss
│   └── index.pkl
│
├── requirements.txt             # Python dependencies
├── demo.html                    # Interactive project demo
└── README.md                    # This file
```

---

## ⚙️ Installation

### 1. Clone the repository
```bash
git clone https://github.com/gowthamreddy-dev/AI-Powered-Market-Trend-Consumer-Sentiment-Forecaster-.git
cd AI-Powered-Market-Trend-Consumer-Sentiment-Forecaster-
```

### 2. Install dependencies
```bash
pip install streamlit pandas numpy plotly matplotlib wordcloud fpdf2 openpyxl
pip install transformers torch bertopic sentence-transformers scikit-learn
pip install langchain==0.3.25 langchain-groq==0.3.2 langchain-community==0.3.24 langchain-huggingface==0.1.2
pip install faiss-cpu
```

### 3. Set up Groq API Key
Get your free API key at 👉 [https://console.groq.com](https://console.groq.com)

Open `Week3_rag_pipeline.py` and set your key on line 10:
```python
GROQ_API_KEY = "your_groq_api_key_here"
```

### 4. Download Dataset
Download **Amazon Fine Food Reviews** from Kaggle:
👉 [https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews)

Place `Reviews.csv` in the project folder.

---

## ▶️ How to Run

### Run the full integrated app:
```bash
cd "path/to/project/folder"
streamlit run week6_integrated_app.py
```

### Run individual modules step by step:
```bash
# Week 1 — Data Pipeline
python Week1_data_pipeline.py

# Week 2 — Sentiment & Topic Modeling
python Week2_sentiment_topics.py

# Week 3 — RAG Pipeline (requires GROQ_API_KEY)
python Week3_rag_pipeline.py

# Week 5 — Alerts & Reports
python week5_alerts_reports.py
```

---

## 👥 User Roles

| Role | Username | Password | Access |
|------|----------|----------|--------|
| 🔴 **Admin** | `admin` | `admin123` | Full access — all tabs, reports, alerts |
| 🔵 **Analyst** | `analyst` | `analyst123` | Sentiment, Topics, AI Insights |
| 🟢 **Marketing** | `marketing` | `market123` | Overview and Topics only |
| 🟡 **Intern** | `intern` | `intern123` | Read-only Overview |

---

## 📦 Modules

### Week 1 — Data Pipeline
- Loads 568,454 Amazon Fine Food Reviews
- Cleans nulls, duplicates, normalizes text
- Generates sentiment labels from star ratings
- Creates 5,000-row sample for AI processing
- **Output:** `cleaned_reviews.csv`, `sample_reviews.csv`

### Week 2 — AI Sentiment & Topic Modeling
- Runs DistilBERT (`distilbert-base-uncased-finetuned-sst-2-english`)
- 97% average confidence on 5,000 reviews
- BERTopic extracts 8 consumer topic clusters
- **Output:** `sentiment_results.csv`, `topics_summary.csv`

### Week 3 — RAG Pipeline
- Embeds 500 reviews using `all-MiniLM-L6-v2`
- Stores vectors in FAISS index
- Answers natural language questions using Groq LLaMA
- **Output:** `rag_insights.csv`, `faiss_index/`

### Week 4 — Dashboard
- 5-tab Streamlit app with sidebar filters
- Rating distribution, sentiment donut, trend lines
- Word clouds, confidence histograms, box plots

### Week 5 — Alerts & Reports
- Auto-detects sentiment spikes and drops
- Generates 4-sheet Excel report
- Generates professional PDF executive report

### Week 6 — Full Integration
- All modules combined into one unified app
- Role-based login system with 4 user types
- One-click report downloads from sidebar

### Week 7 — Cloud Deployment
- Pushed to GitHub
- Deployed on Streamlit Community Cloud
- Live public URL accessible worldwide

---

## 📊 Dataset

| Property | Value |
|----------|-------|
| **Name** | Amazon Fine Food Reviews |
| **Source** | Kaggle / Stanford SNAP |
| **Total Reviews** | 568,454 |
| **Analyzed Sample** | 5,000 |
| **Date Range** | 2004 – 2012 |
| **Positive Reviews** | 77.9% |
| **Negative Reviews** | 14.5% |
| **Neutral Reviews** | 7.6% |

---

## 🗓️ Milestones

| Week | Milestone | Status |
|------|-----------|--------|
| Week 1 | Data Pipeline — Scraping, cleaning, normalization | ✅ Complete |
| Week 2 | AI Sentiment & Topic Modeling — DistilBERT + BERTopic | ✅ Complete |
| Week 3 | RAG Pipeline — LangChain + FAISS + Groq | ✅ Complete |
| Week 4 | Dashboard — Streamlit + Plotly | ✅ Complete |
| Week 5 | Alerts & Reports — PDF + Excel generation | ✅ Complete |
| Week 6 | Full Integration — Login + Unified app | ✅ Complete |
| Week 7 | Cloud Deployment — GitHub + Streamlit Cloud | ✅ Complete |

---

## 📈 Key Results

- ✅ **568,454** reviews loaded and cleaned
- ✅ **5,000** reviews analyzed with AI (97% confidence)
- ✅ **8 topics** discovered by BERTopic
- ✅ **RAG pipeline** answering natural language queries
- ✅ **Live dashboard** deployed on Streamlit Cloud
- ✅ **Role-based login** with 4 user types
- ✅ **PDF + Excel** reports auto-generated

---

## 🔑 Key Fixes & Lessons Learned

| Issue | Fix |
|-------|-----|
| ChromaDB needs C++ Build Tools | Replaced with FAISS |
| Groq model decommissioned | Use `llama-3.3-70b-versatile` |
| fpdf2 crashes on emojis | Strip with `to_ascii()` helper |
| Large files blocked GitHub push | Added `.gitignore` for CSV/SQLite |
| PowerShell `&&` not working | Use `;` as separator |

---

## 🙏 Acknowledgements

- [Kaggle — Amazon Fine Food Reviews](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews)
- [HuggingFace Transformers](https://huggingface.co/)
- [LangChain](https://langchain.com/)
- [Groq](https://groq.com/)
- [Streamlit](https://streamlit.io/)
- [BERTopic](https://maartengr.github.io/BERTopic/)

---

## 📄 License

This project is licensed under the MIT License.

---

<div align="center">
  Built with ❤️ by <b>gowthamreddy-dev</b> | Internship Project 2026
</div>
