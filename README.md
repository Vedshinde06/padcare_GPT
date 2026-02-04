
---

```markdown
# 🌱 PadCare GPT: Retrieval-Augmented AI Assistant

> **An intelligent, halluncination-free AI assistant built using public PadCare Labs information for the AI Intern Interview Assignment.**

---

## 📌 Project Overview

**PadCare GPT** is a high-precision RAG (Retrieval-Augmented Generation) system designed to act as an internal knowledge assistant. It empowers PadCare’s team to instantly access company data, generate impact-driven content, and verify factual information—all while ensuring **zero leakage** of external, unverified knowledge.

### 🎯 Key Capabilities
* **Factual Q&A:** Answers "What problem does PadCare solve?" with 100% grounded accuracy.
* **Content Generation:** Drafts investor pitches and LinkedIn posts based on real impact metrics.
* **Traceability:** Every response includes direct **source citations** from internal documents.
* **Safety First:** Engineered to say "I don't know" rather than hallucinating when data is missing.

---

## 🧠 System Architecture

The assistant follows a modular RAG pipeline to ensure performance and reliability without using proprietary (paid) APIs.



1.  **Ingestion:** Public PadCare data is cleaned and structured into intent-based segments.
2.  **Vectorization:** Text is chunked (300–500 tokens) and converted into embeddings using `all-MiniLM-L6-v2`.
3.  **Storage:** Embeddings are indexed in a local **FAISS** vector store.
4.  **Retrieval:** Relevant context is pulled based on semantic similarity to the user query.
5.  **Generation:** An open-source LLM (`Zephyr-7B`) synthesizes the final answer using *only* the retrieved context.

---

## 🛠️ Tech Stack

| Category | Tools |
| :--- | :--- |
| **Language** | Python |
| **Orchestration** | LangChain (LCEL) |
| **Vector Database** | FAISS (Local) |
| **Embeddings** | SentenceTransformers |
| **LLM** | Hugging Face Inference API (`zephyr-7b-beta`) |
| **Frontend** | Streamlit |

---

## 📂 Data Engineering

The system relies on a structured hierarchy of public data to ensure high-quality retrieval:

```text
padcare_data/
├── company_overview.txt        # Mission, Vision, Values
├── problem_statement.txt       # Menstrual waste crisis stats
├── process_and_technology.txt  # Technical recycling breakdown
├── impact_metrics.txt          # ESG and sustainability data
└── [Other public documents...]

```

---

## 🚀 Getting Started

### 1. Installation

```bash
git clone <your-github-repo-url>
cd padcare_GPT
python -m venv venv
source venv/bin/activate  # macOS/Linux or venv\Scripts\activate for Windows
pip install -r requirements.txt

```

### 2. Configuration

Create a `.env` file in the root directory:

```env
HUGGINGFACEHUB_API_TOKEN=your_huggingface_token_here

```

### 3. Ingestion & Launch

```bash
# Process documents and create vector store
python ingest.py

# Launch the UI
streamlit run app.py

```

---

## 🧪 Evaluation Examples

| Query | Expected Outcome |
| --- | --- |
| "What is Rebirth by PadCare?" | Accurate description of the sustainable brand + Citations. |
| "Write a 5-bullet summary of impact." | Data-driven bullet points based on `impact_metrics.txt`. |
| "Who is the Prime Minister of UK?" | "I'm sorry, I don't have that information." (Prevents Hallucination). |

---

## 📈 Future Roadmap

* [ ] **Multi-modal Support:** Ingest PDF reports and technical diagrams.
* [ ] **Confidence Scoring:** Display a "Match Score" for each retrieved document.
* [ ] **Vernacular Support:** Enable queries in Marathi and Hindi for broader accessibility.
* [ ] **Unit Testing:** Implement automated tests for retrieval accuracy (RAGAS).

---

