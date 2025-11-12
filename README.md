## 🧭 **Project Description**

This project is an **AI-powered Hybrid Travel Assistant** that integrates **Graph Databases (Neo4j)**, **Vector Databases (Pinecone)**, and **LLMs (Groq API)** to deliver **context-aware, semantic travel recommendations**.

It is trained on a structured dataset of **Vietnam travel destinations**, including cities, attractions, activities, and hotels — allowing users to ask natural-language questions like:

> “What are the best activities near Ha Long Bay?”
> “Suggest a 3-day itinerary in Hanoi including cultural sites.”
> “When is the best time to visit Da Nang beaches?”

The system retrieves **semantically relevant nodes** from Pinecone using **Hugging Face embeddings**, enriches responses with **graph relationships** from Neo4j (e.g., *City → Attraction → Activity*), and generates natural answers via **Groq’s LLM**.

---

## 🧩 **Key Features**

✅ **Hybrid RAG Architecture** – Combines semantic similarity search (Pinecone) and knowledge graph reasoning (Neo4j).
✅ **Vector Search** – Uses Sentence-Transformers (MiniLM-L6-v2) for 384-dim embeddings.
✅ **Graph-Aware Reasoning** – Neo4j stores entity relationships and supports constraint-based querying.
✅ **Groq LLM Integration** – Summarizes semantic and graph context into natural, contextually accurate answers.
✅ **Data Visualization** – PyVis-based graph visualization for exploration of relationships.
✅ **Modular Design** – Independent modules for data loading, vector indexing, visualization, and interactive chat.

---

## 🏗️ **System Architecture**

```
             ┌─────────────────────┐
             │ Vietnam JSON Dataset │
             └──────────┬──────────┘
                        │
                        ▼
               ┌───────────────────┐
               │ Neo4j Graph Loader│
               │ (Cities, Hotels,  │
               │ Attractions, etc.)│
               └─────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │ Pinecone Indexer │
                │ (Hugging Face    │
                │ embeddings)      │
                └────────┬─────────┘
                         │
                         ▼
                 ┌──────────────┐
                 │ Groq LLM API │
                 │ (Semantic QA)│
                 └──────────────┘
                         │
                         ▼
            ┌──────────────────────────────┐
            │ Interactive Travel Assistant │
            │ (Hybrid RAG Chat Interface)  │
            └──────────────────────────────┘
```

---

## 🗃️ **Project Structure**

```
📂 hybrid-travel-assistant/
├── vietnam_travel_dataset.json        # Source dataset
├── load_to_neo4j.py                   # Loads entities & relationships into Neo4j
├── pinecone_upload_hf_groq.py         # Embeds & uploads data to Pinecone
├── visualize_graph.py                 # Visualizes the Neo4j graph using PyVis
├── hybrid_chat.py                     # Main interactive hybrid chat system
├── requirements.txt                   # Dependencies
└── README.md                          # Documentation
```

---

## ⚙️ **Setup Instructions**

### 1️⃣ **Clone the Repository**

```bash
git clone https://github.com/<your-username>/hybrid-travel-assistant.git
cd hybrid-travel-assistant
```

### 2️⃣ **Install Dependencies**

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install neo4j pinecone pyvis groq torch transformers tqdm
```

### 3️⃣ **Set Your API Keys**

Create a `.env` file or define them in your script:

```bash
NEO4J_URI="neo4j+s://3102fef0.databases.neo4j.io"
NEO4J_USER="neo4j"
NEO4J_PASSWORD="<your-neo4j-password>"

PINECONE_API_KEY="<your-pinecone-key>"
PINECONE_CLOUD="aws"
PINECONE_ENV="us-east-1"
PINECONE_INDEX_NAME="vietnam-travel"

GROQ_API_KEY="<your-groq-api-key>"
```

---

## 🚀 **How to Run**

### Step 1️⃣ – Load Data into Neo4j

```bash
python load_to_neo4j.py
```

This creates entity nodes and relationships (Cities, Attractions, Hotels, Activities) in Neo4j.

### Step 2️⃣ – Upload Embeddings to Pinecone

```bash
python pinecone_upload_hf_groq.py
```

This script generates sentence embeddings using `sentence-transformers/all-MiniLM-L6-v2` and uploads them to Pinecone.

### Step 3️⃣ – Visualize Graph (Optional)

```bash
python visualize_graph.py
```

Outputs an interactive HTML visualization (`neo4j_viz.html`).

### Step 4️⃣ – Run the Hybrid Assistant

```bash
python hybrid_chat.py
```

You’ll get an interactive CLI:

```
🌍 HYBRID TRAVEL ASSISTANT
Ask questions about destinations, attractions, and travel tips.
Type 'exit' or 'quit' to end the session.

You: Suggest an itinerary for Hanoi in 2 days
Assistant:
------------------------------------------------------------
Day 1: Visit Hoan Kiem Lake [A102], explore Old Quarter [A203].
Day 2: Cultural tour at Temple of Literature [A108] and Fine Arts Museum [A207].
------------------------------------------------------------
```

---

## 🧠 **Core Concepts**

* **Neo4j Graph** – Models relational structure (City–Attraction–Activity).
* **Pinecone Index** – Provides high-dimensional semantic retrieval.
* **Groq LLM** – Generates natural language summaries and itinerary recommendations.
* **Hybrid Retrieval** – Combines symbolic graph facts + dense semantic matches for contextual precision.

---

## 📈 **Example Use Cases**

* “Find must-visit attractions in Central Vietnam.”
* “What are the best beaches and hotels in Da Nang?”
* “Plan a cultural tour itinerary across Hanoi.”
* “Show connections between Ha Long Bay and nearby activities.”

---

## 🧮 **Tech Stack**

| Component           | Technology                               |
| ------------------- | ---------------------------------------- |
| **Graph DB**        | Neo4j AuraDB                             |
| **Vector DB**       | Pinecone                                 |
| **Embedding Model** | `sentence-transformers/all-MiniLM-L6-v2` |
| **LLM**             | Groq API (Mixtral / LLaMA2)              |
| **Frameworks**      | PyTorch, Transformers                    |
| **Visualization**   | PyVis, NetworkX                          |
| **Language**        | Python 3.10+                             |

---

## 📚 **Future Improvements**

* ✅ Add Streamlit UI for visual chat interface
* ✅ Integrate multilingual embeddings
* 🔜 Include itinerary generation templates
* 🔜 Expand dataset beyond Vietnam (Southeast Asia module)
* 🔜 Integrate OpenAI GPT-4 for comparative benchmarking

---

## 🏆 **Acknowledgements**

* [Neo4j AuraDB](https://neo4j.com/cloud/platform/aura-graph-database/)
* [Pinecone](https://www.pinecone.io/)
* [Groq API](https://groq.com/)
* [Hugging Face Transformers](https://huggingface.co/sentence-transformers)
* [PyVis](https://pyvis.readthedocs.io/)

---
