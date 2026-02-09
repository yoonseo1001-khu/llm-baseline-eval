\# Benchmarks



This document summarizes the benchmark datasets used in this project, including task

definitions, input/output formats, and evaluation metrics.



---



\## 1) MedQA (USMLE-style)



\*\*Source\*\*

\- Hugging Face: `bigbio/med\_qa`

\- Configuration: `med\_qa\_en\_source`



\### Task

\- Multiple-choice clinical question answering



\### Input

\- Clinical question text

\- Five answer options labeled A–E



\### Output

\- Single answer choice in {A, B, C, D, E}



\### Metric

\- Accuracy (exact match)



\### Notes

\- Standard splits: train / validation / test

\- This repository supports evaluation on any split



---



\## 2) HealthBench (umbrella benchmark)



HealthBench is treated as an \*\*umbrella benchmark\*\* for clinical reasoning and healthcare

decision-making tasks rather than a single fixed dataset identifier.



\### Typical tasks

\- Open-ended clinical question answering

\- Clinical reasoning and explanation generation



\### Input

\- Clinical question (optionally with context)



\### Output

\- Free-text answer



\### Metrics

\- ROUGE-L (baseline)

\- Task-specific metrics depending on dataset definition



\### Implementation

\- Generic loader interface:

&nbsp; ```python

&nbsp; load\_healthbench(dataset\_id, \*\*kwargs)



\## Closed-source datasets (pending)



\### JAMA Clinical Q\&A

\- Access: research license

\- Planned location: BigPurple (local filesystem)



\### ReMedE

\- Focus: medical reasoning and decision-making

\- Access: research license

\- Planned location: BigPurple



These datasets will be loaded from local paths and will not be committed to this repository.



