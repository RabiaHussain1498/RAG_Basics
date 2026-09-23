# RAG Basics — Chunking, Embeddings, Vector Databases, and Retrieval Evaluation

Week 8 Day 1 kata: hands-on fundamentals of Retrieval-Augmented Generation (RAG),
covering chunking, embeddings, vector search with Qdrant, hybrid search
limitations, and retrieval evaluation (precision@k / recall@k).

Sample document: an excerpt from AISI's public incident report on an AI agent's
unsanctioned cyber behaviour during a controlled evaluation.

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Open `notebook.ipynb` and run all cells top to bottom.

## Contents

- **Part A — Chunking & embeddings by hand**
  Fixed-size chunking with and without overlap on a real document; found and
  verified a real sentence split across chunk boundaries in the no-overlap
  version, fixed by 15% overlap. Cosine similarity computed manually with NumPy
  on 3 embedded sentences, confirming semantically similar text scores higher.

- **Part B — Vector database (Qdrant)**
  Local in-memory Qdrant collection with 10 real sentences embedded via
  `all-MiniLM-L6-v2`. Query tested and top result verified correct by inspection.

- **Part C — Hybrid search gap & retrieval evaluation**
  Demonstrated a case where exact-ID search returns a weak semantic match score,
  illustrating why hybrid (semantic + keyword) search matters. Precision@3 and
  recall@3 computed by hand across 3 queries on the same small corpus.

## Project structure

- data/sample_document.txt — source text used for chunking
- notebook.ipynb — all kata work (Parts A, B, C)
- requirements.txt — direct dependencies


## Key findings

- Overlap chunking prevented a sentence describing a key finding from being
  split across chunk boundaries, no-overlap chunking did split it.
- Semantically similar sentences scored ~5x higher in cosine similarity than
  unrelated ones.
- An exact-ID query technically retrieved the right sentence, but with a
  notably weak similarity score, showing embeddings alone are a fragile way
  to handle exact-match lookups.
- Precision@3 dropped for topically-related queries where multiple sentences
  shared vocabulary but differed in actual relevance, a concrete illustration
  of retrieval precision loss in a real (if small) corpus.