# 🌐 GraphRAG — AI Copyright & Governance Knowledge Graph

An advanced **GraphRAG** (Graph Retrieval-Augmented Generation) pipeline that maps the complex relationships between AI labs, legal cases, and global regulations.

---

## 🧠 GraphRAG vs. Vector RAG: Why the Switch?

Traditional RAG (Vector-based) is like having a library of loose pages; GraphRAG is like having the library's index, table of contents, and a librarian who has already read every book.

### ❌ The "Vector RAG" Limitation
Standard RAG relies on **Vector Similarity**. It slices documents into chunks and finds the ones that look most like your question. 
- **The Problem:** It can't "connect the dots." If legal evidence is on Page 10 and the defendant's name is on Page 500, Vector RAG often fails to bridge that gap. 
- **The Fail Case:** Global questions like *"What are the common strategies used by plaintiffs in these 50 different lawsuits?"* usually result in fragmented, incomplete answers because the LLM only sees a few disconnected snippets at a time.

### ✅ The "GraphRAG" Solution
GraphRAG builds a **Structured Knowledge Mesh** before you ever ask a question.
1.  **Relationship Awareness:** It understands that `OpenAI` is a *Defendant* in `NYT v. OpenAI` and an *Aggregator* of `Training Data`. These links are explicit, not just "statistically similar."
2.  **Global Summarization:** It groups related entities into **Communities** (e.g., "Copyright Lawsuits", "EU Regulations") and generates summaries for each. 
3.  **Synthesis vs. Retrieval:** Instead of fetching raw text chunks, it queries these **pre-summarized communities**. This allows it to answer "big picture" questions by synthesizing information from across the entire dataset simultaneously.

---

## 🧬 How it Works (The Mechanics)

### 1. The Extraction phase (Ontology-Driven)
We don't just extract text; we extract **meaningful triplets**.
*   **Source:** `GitHub`
*   **Relation:** `DEFENDANT_IN`
*   **Target:** `Copilot Lawsuit`
*   *Plus:* A detailed description of **why** they are related.

### 2. The Clustering Phase (Community Detection)
Using the **Leiden Algorithm**, the system detects "tribes" of information. Even if two documents don't share keywords, if they share common entities (like mentioning the same lawyer or law), they are grouped together.

### 3. The Query Phase (Map-Reduce)
- **Map:** Your question is sent to every relevant community summary in parallel.
- **Reduce:** The final model (`gpt-4o`) takes all those community-level answers and filters out the noise to give you one authoritative, global response.

---

## 🚀 The Pipeline at a Glance

| Feature | Vector RAG | **GraphRAG** |
| :--- | :--- | :--- |
| **Data Structure** | Unstructured Text Chunks | Structured Entity-Relation Graph |
| **Search Method** | Semantic Similarity (Floating points) | Graph Traversal + Community Summary |
| **Best Question Type** | "What did X say on page 5?" | "How is X's policy impacting Y globally?" |
| **Context Window** | Limited to top-K chunks | Holistic view of all data communities |

---

## 📂 Project Structure

```bash
graphrag/
├── scrape_info.ipynb              # 🔍 Data Sourcing: Web & YouTube scraping
├── graphrag_ai_copyright.ipynb    # 🏗️ The Pipeline: Graph build, clustering, & querying
├── ai_copyright_dataset.csv       # 📊 Source Data: 800+ enriched news rows
├── graph_data.json                # 🕸️ Knowledge Mesh: Nodes, Edges, & Community IDs
├── ai_copyright_graph.html        # 🎨 Deep Discovery: The interactive visual UI
└── graph_template.html            # 🛠️ D3.js UI Template
```

---

## ⚙️ Setup & Installation

1. **Environment:**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # Or .venv\Scripts\activate on Windows
   ```

2. **Dependencies:**
   ```bash
   pip install llama-index llama-index-llms-openai graspologic \
               pandas nest-asyncio python-dotenv \
               google-search-results trafilatura youtube_transcript_api requests
   ```

3. **Secrets:** Create a `.env` file:
   ```env
   SERPAPI_KEY=your_key
   OPENAI_API_KEY=your_key
   ```

---

*Built with ❤️ for AI researchers and legal tech enthusiasts to bridge the gap between Big Data and True Insight.*
