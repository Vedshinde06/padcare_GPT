# 🌱 PadCare GPT  
### An AI Assistant Built Using Public PadCare Information

---

## 📌 Overview

**PadCare GPT** is a **retrieval-augmented AI assistant** designed to answer questions about **PadCare Labs** using **only publicly available information**.

This project was built as part of the **AI Intern interview assignment** and is intended to act as an **internal knowledge assistant** for PadCare’s team and leadership.

It helps users:
- Understand PadCare’s mission and impact  
- Generate structured content (summaries, pitches, LinkedIn posts)  
- Ask factual questions with confidence  

The system prioritizes **accuracy, transparency, and non-hallucination**.

---

## 🎯 What the Assistant Can Do

PadCare GPT can handle prompts such as:

- *What problem does PadCare solve?*  
- *Explain PadCare’s process in simple words.*  
- *Create a short investor pitch for PadCare.*  
- *Write a LinkedIn post about PadCare’s impact.*  
- *Summarize PadCare’s work in 5 bullet points.*

Each response is:

- ✅ Grounded in retrieved documents  
- ✅ Generated using an open-source LLM  
- ✅ Returned with source citations  

---

## 🧠 System Architecture (High Level)

PadCare GPT follows a **Retrieval-Augmented Generation (RAG)** pipeline:

Public PadCare Data
↓
Text Cleaning & Structuring
↓
Chunking (300–500 tokens)
↓
Vector Embeddings (SentenceTransformers)
↓
FAISS Vector Store
↓
Retriever
↓
LLM (Hugging Face Inference)
↓
Answer + Source Citations


### Why RAG?
- Prevents hallucinations  
- Ensures factual accuracy  
- Allows traceability of answers  

---

## 📂 Data Sources Used (Public Only)

All data was collected strictly from **publicly available PadCare sources**, including:

- Official PadCare website (About, Technology, Impact, CSR)  
- Public blogs and explainer pages  
- Publicly listed awards and recognitions  
- **Rebirth** (PadCare’s sustainable brand) product descriptions  
- Public founder story and mission statements  

No private, internal, or proprietary data was used.

---

## 📁 Data Organization

Public content was structured into **intent-based text files**:

padcare_data/
├── company_overview.txt
├── problem_statement.txt
├── process_and_technology.txt
├── impact_metrics.txt
├── awards_and_recognition.txt
├── founder_story.txt
├── rebirth_brand.txt
├── csr_and_esg.txt
└── investor_pitch.txt


This structure makes retrieval more precise and explainable.

---

## ⚙️ Tech Stack (All Free & Open-Source)

### Core
- Python  
- Streamlit – lightweight internal UI  

### RAG & Orchestration
- LangChain (LCEL-based)  
- FAISS – local vector database  

### Embeddings
- SentenceTransformers  
- `all-MiniLM-L6-v2`  

### LLM (Inference)
- Hugging Face Inference API  
- Model: `HuggingFaceH4/zephyr-7b-beta`  
  *(chat-optimized, open-source)*  

### Security
- API keys stored in `.env`  
- `.env` excluded via `.gitignore`  

---

## 🔒 Hallucination Prevention & Safety

PadCare GPT is intentionally designed to **avoid hallucinations**:

- Retrieval-first architecture  
- Answers generated **only from retrieved context**  
- System instruction enforces:  
  > *“If the answer is not in the provided context, say you don’t know.”*  
- Source documents are displayed with each response  

This makes the assistant safe for **internal, leadership, and executive use**.

---

## 🚀 How to Run the Project Locally

### 1️⃣ Clone the Repository
```bash
git clone <your-github-repo-url>
cd padcare_GPT
2️⃣ Create & Activate Virtual Environment
Windows

python -m venv myenv
myenv\Scripts\activate
macOS / Linux

python -m venv myenv
source myenv/bin/activate
3️⃣ Install Dependencies
pip install -r requirements.txt
4️⃣ Set Environment Variables
Create a .env file in the project root:

HUGGINGFACEHUB_API_TOKEN=your_huggingface_token_here
⚠️ Ensure .env is added to .gitignore.

5️⃣ Ingest Public Data (One-Time Step)
This step:

Loads public PadCare documents

Chunks the text

Generates embeddings

Stores them in FAISS

python ingest.py
A vectorstore/ directory will be created.

6️⃣ Run the App
streamlit run app.py
The app will open in your browser.

🧪 Example Test Prompts
Try these after launch:

What problem does PadCare solve?

Explain PadCare’s recycling process in simple words.

Create a short investor pitch for PadCare.

Write a LinkedIn post about PadCare’s environmental impact.

What is Rebirth by PadCare?

Each response includes source citations.

📈 Future Improvements
With more time, I would:

Add document-level confidence scoring

Enable admin-side data updates without re-deployment

Add separate Marketing and Technical response modes

Improve UI with chat history and filters

Add multilingual support for Indian languages

Add automated tests for ingestion and retrieval

✅ Assignment Requirements Checklist
✔ Uses only publicly available information
✔ No paid tools or proprietary APIs
✔ Fully open-source tech stack
✔ Simple and functional UI
✔ Clear explanation of approach
✔ Demonstrates system thinking

🙌 Final Note
PadCare GPT was built with a strong focus on:

Accuracy over flashiness

System design over model obsession

Real-world usability

This project demonstrates how an AI intern would realistically design and implement a production-safe internal assistant under real-world constraints.
