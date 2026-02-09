\# Methodology



This document describes the evaluation methodology for encoder-based baselines and small

generative language model baselines on clinical benchmarks.



---



\## Goals

\- Provide a unified and reproducible evaluation pipeline across benchmarks

\- Compare encoder-based baselines with small open-weight LLMs (≤7B parameters)

\- Enable future extensions such as routing, cascading, and ensemble-based composition



---



\## Baseline types



\### 1) Random baseline (sanity check)

\- Purpose: verify that dataset loading, splits, evaluation, and result export are correct

\- Expected performance: near chance level (e.g., ~0.20 for 5-choice MCQ)



---



\### 2) Encoder baseline (bi-encoder)

\- Method: encode the question and each answer option independently

\- Scoring: cosine similarity between question embedding and option embeddings

\- Prediction: select the option with the highest similarity score



\*\*Pros\*\*

\- Fast inference

\- Scales well to large datasets

\- No generation required



\*\*Limitations\*\*

\- Limited reasoning ability for multi-step clinical questions



---



\### 3) Small generative LLM baseline

Two scoring approaches are supported:



1\. \*\*Generation + parsing\*\*

&nbsp;  - Generate an answer and parse the output to extract A–E

&nbsp;  - Sensitive to output formatting



2\. \*\*Logit-choice (default)\*\*

&nbsp;  - Score next-token logits for {A, B, C, D, E}

&nbsp;  - Select the option with the highest probability

&nbsp;  - More stable and reproducible



---



\## Prompting strategy (MedQA)

\- Input format: clinical question + options (A–E)

\- Instruction: respond with only one answer choice

\- For logit-choice: score logits after a fixed prompt suffix (e.g., `Answer:`)



---



\## Evaluation outputs

\- Results are saved as JSON files under `results/`

\- Each result file includes:

&nbsp; - model name

&nbsp; - dataset and split

&nbsp; - number of evaluated samples

&nbsp; - accuracy (and parsing error rate if applicable)



---



\## Future extensions

\- \*\*Routing\*\*: select specialized models based on question features

\- \*\*Cascading\*\*: escalate from smaller to larger models based on confidence

\- \*\*Ensembling\*\*: aggregate predictions from multiple small models



