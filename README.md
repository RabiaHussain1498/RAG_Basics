# Chunking Strategies for RAG

This project explores and compares different text chunking strategies used in Retrieval-Augmented Generation (RAG).

## Chunking Strategies

The notebook implements and compares:

* Fixed-size chunking
* Sentence chunking
* Paragraph chunking
* Semantic chunking
* Recursive chunking

Each strategy is applied to the same document and evaluated using:

* Number of chunks
* Average token count
* Standard deviation
* Minimum chunk size
* Maximum chunk size

## Results

| Strategy   | # Chunks | Avg Tokens | Std Dev | Min | Max |
| ---------- | -------: | ---------: | ------: | --: | --: |
| Fixed-size |       16 |      195.4 |    17.9 | 126 | 200 |
| Sentence   |       44 |       80.3 |    22.8 |  31 | 123 |
| Paragraph  |       46 |       58.2 |    27.7 |  17 | 147 |
| Semantic   |       21 |      127.4 |    94.3 |   1 | 248 |
| Recursive  |       14 |      220.0 |    45.6 | 105 | 250 |

## Conclusion

Recursive chunking was selected as the most suitable approach for this use case because it provides a good balance between chunk size, document structure, and number of chunks while keeping the process simple.

## Files

* `chunking_strategies.ipynb` — Python implementation and comparison of all chunking strategies.
* `requirements.txt` — Required Python packages.

## How to Run

Install the required packages:

```bash
pip install -r requirements.txt
```

Then open and run:

```text
chunking_strategies.ipynb
```
