🌱 PadCare GPT

An AI Assistant Built Using Public PadCare Information

📌 Overview

PadCare GPT is a retrieval-augmented AI assistant designed to answer questions about PadCare Labs using only publicly available information.

The project was built as part of the AI Intern interview assignment and is intended to act as an internal knowledge assistant that PadCare’s team or leadership could use to:

Understand PadCare’s mission and impact

Generate content (summaries, pitches, LinkedIn posts)

Answer factual questions safely and accurately

The system is designed with accuracy, transparency, and non-hallucination as first-class principles.

🎯 What the Assistant Can Do

PadCare GPT can reliably handle prompts such as:

“What problem does PadCare solve?”

“Explain PadCare’s process in simple words.”

“Create a short investor pitch for PadCare.”

“Write a LinkedIn post about PadCare’s impact.”

“Summarize PadCare’s work in 5 bullet points.”

Each answer is:

Grounded in retrieved documents

Generated using an open-source LLM

Returned with source citations

🧠 System Architecture (High Level)

PadCare GPT uses a Retrieval-Augmented Generation (RAG) approach.

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


This ensures:

No hallucinations

No external knowledge leakage

Full traceability of answers

📂 Data Sources Used (Public Only)

All data was collected from publicly available PadCare sources, including:

Official PadCare website (About, Technology, Impact, CSR)

Public blogs and explainer pages

Publicly listed awards and recognitions

Rebirth (PadCare’s sustainable brand) product descriptions

Public founder story and mission statements

📁 These were structured into intent-based documents:

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

⚙️ Tech Stack (All Free / Open-Source)
Core

Python

Streamlit – simple internal UI

RAG & Orchestration

LangChain (v1.x, LCEL-based)

FAISS – local vector database

Embeddings

SentenceTransformers

all-MiniLM-L6-v2

LLM (Inference)

Hugging Face Inference API

Model: HuggingFaceH4/zephyr-7b-beta (chat-optimized, open-source)

Security

API keys stored in .env

.env excluded via .gitignore

🔒 Hallucination Prevention & Safety

PadCare GPT is explicitly designed to avoid hallucinations:

Uses retrieval-first architecture

Answers are generated only from retrieved context

System prompt instructs:

“If the answer is not in the provided context, say you don’t know.”

Source files used for each response are displayed

This makes the assistant safe for internal and executive use.

🚀 How to Run the Project Locally
1️⃣ Clone the Repository
git clone <your-github-repo-url>
cd padcare_GPT

2️⃣ Create and Activate Virtual Environment

Windows (PowerShell):

python -m venv myenv
myenv\Scripts\activate


macOS / Linux:

python -m venv myenv
source myenv/bin/activate

3️⃣ Install Dependencies
pip install -r requirements.txt

4️⃣ Set Up Environment Variables

Create a .env file in the project root:

HUGGINGFACEHUB_API_TOKEN=your_huggingface_token_here


⚠️ Ensure .env is listed in .gitignore.

5️⃣ Ingest the Data (One-Time Step)

This step:

Loads public PadCare documents

Chunks them

Generates embeddings

Stores them in FAISS

python ingest.py


After this, a vectorstore/ folder will be created.

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

Each response will include cited sources.

📈 What I’d Improve With More Time

If given more time, I would:

Add document-level confidence scoring

Enable admin-side data updates without re-deployment

Add separate “Marketing” vs “Technical” response modes

Improve UI with chat history and filters

Add multilingual support for Indian languages

Add unit tests for ingestion and retrieval

✅ Assignment Requirements Checklist

✔ Uses only publicly available information
✔ No paid tools or proprietary APIs
✔ Open-source / free tech stack
✔ Simple but functional UI
✔ Clear explanation of approach
✔ Demonstrates problem-solving and system thinking

🙌 Final Note

PadCare GPT was built with a strong focus on:

Accuracy over flashiness

System design over model obsession

Real-world usability

The project reflects how an AI intern would realistically build a production-safe internal assistant under time constraints.
