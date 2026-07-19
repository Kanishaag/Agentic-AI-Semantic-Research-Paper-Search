# AI Research Paper Intelligence System 🤖📄

An advanced semantic literature discovery and analysis portal built using **Agentic AI architecture** and **NLP Transformers**. The system optimizes the research workflow by allowing users to perform deep semantic lookups over text databases and interact with literature via an autonomous agent pipeline.

---

## 🚀 Core Features
*   **Semantic Search Engine:** Finds research papers based on conceptual meaning rather than basic keyword matching using normalized vector retrieval.
*   **Autonomous Agent Framework:** A LangChain tool-calling loop powered by Llama 3.1 via the Groq Inference Engine to determine the best execution path dynamically.
*   **Document Summarization:** Auto-generates high-density summaries of paper abstracts utilizing a specialized convolutional encoder-decoder pipeline.
*   **Keyword & Entity Extraction:** Extracts top-k keyphrases and isolates specialized machine learning entities (models, datasets, and frameworks).
*   **Comparative Analysis:** Leverages the LLM core to perform objective, side-by-side methodology and performance comparisons between different papers.
*   **Conversational Continuity:** Integrates local state checkpoints so the agent remembers previous queries for contextual follow-up questions.

---

## 📁 Dataset & Preprocessing
*   **Source Data:** `CShorten/ML-ArXiv-Papers` fetched directly from Hugging Face.
*   **Volume Used:** Filtered strictly to the first **15,000 papers** to optimize in-memory performance and vector processing speeds.
*   **Pipeline Clean:** Merges the `title` and `abstract` properties into a unified `paper_text` string, scrubbing structural newline breaks and extra whitespace padding.

---

## 🛠️ Tech Stack & Architecture

### Core Engineering
*   **Languages & Data:** Python, Pandas, NumPy, Scikit-learn
*   **Vector Search & Indexing:** FAISS (Facebook AI Similarity Search - `IndexFlatIP`)
*   **Agent Orchestration:** LangChain & LangGraph

### Production Models
| Model / Pipeline | Role in Architecture |
| :--- | :--- |
| **`all-MiniLM-L6-v2`** | Generates 384-dimensional dense semantic text embeddings |
| **`llama-3.1-8b-instant` (Groq)** | Runs agentic reasoning, tool routing, and comparative analysis |
| **`facebook/bart-large-cnn`** | Compiles crisp, abstractive summaries of retrieved literature |
| **KeyBERT** | Extracts high-relevance technical keyphrases via BERT embeddings |
| **HuggingFace NER Pipeline** | Isolates named entities (e.g., PyTorch, ResNet, training sets) |

---

## ⚙️ Core Workflow & Mechanics

1.  **Vector Processing:** The 15k text documents are converted into normalized embeddings and cached locally as `paper_embeddings.npy`.
2.  **Indexing:** Embeddings are loaded into an inner-product FAISS index (`paper_faiss.index`) for ultra-low latency similarity queries.
3.  **Search Loop:** User Input ➔ Embedding Alignment ➔ FAISS Top-K Retrieval ➔ Extracted Abstract Strings.
4.  **Agent Loop:** LangChain tools wrap individual functions. The Llama 3.1 engine parses user intent, calls the necessary tool pipeline, tracks thoughts via state checkpoints (`MemorySaver`), and renders the final verdict.

---

## 📦 Environment Setup & Security

The system requires an active Groq API token to power the reasoning core. To configure it securely without exposing credentials in the repository code:

1.  Generate an API key via the **[Groq Console](https://console.groq.com/)**.
2.  Open the left-hand **Secrets (🔑)** panel inside your Google Colab interface.
3.  Create a new secret item with the Name: `GROQ_API_KEY`
4.  Paste your token into the Value field and switch the **Notebook access** toggle to **ON**.

---

## 📜 Conclusion
This portal demonstrates the practical integration of vector databases, deep learning transformer pipelines, and autonomous agent frameworks. By shifting the search paradigm from string matching to semantic intent tracking, the platform provides a faster, interactive path for exploring machine learning literature.
