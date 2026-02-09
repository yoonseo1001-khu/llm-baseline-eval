\# Clinical LLM Baseline Evaluation



This repository provides a \*\*unified baseline evaluation framework\*\* for encoder-based models

and small open-weight language models (≤7B parameters) on biomedical and clinical reasoning

benchmarks. The goal is to systematically benchmark small, task-focused models against

larger frontier models, with an emphasis on \*\*clinical feasibility, low latency, and modularity\*\*.



---



\## Benchmarks



\### MedQA (USMLE-style)

\- \*\*Task\*\*: Multiple-choice clinical question answering

\- \*\*Input\*\*: Clinical question with multiple answer options

\- \*\*Output\*\*: Single answer choice (A–E)

\- \*\*Metric\*\*: Accuracy



\### HealthBench

\- \*\*Task\*\*: Open-ended clinical question answering

\- \*\*Input\*\*: Clinical question

\- \*\*Output\*\*: Free-text answer

\- \*\*Metric\*\*: ROUGE-L (or task-specific evaluation metrics)



\*\*Implementation note\*\*



In this project, \*HealthBench\* is treated as an \*\*umbrella benchmark\*\* for clinical reasoning

and healthcare decision-making tasks, rather than a single fixed dataset identifier.



To support flexible HealthBench-style evaluation, this repository provides a generic

dataset adapter that allows plugging in any HealthBench-compatible public dataset

once the appropriate Hugging Face dataset ID is finalized.



```python

from llm\_baseline\_eval.datasets.healthbench import load\_healthbench



ds = load\_healthbench("<HF\_DATASET\_ID\_HERE>")

print(ds)



