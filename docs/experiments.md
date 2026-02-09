\## MedQA baselines



\### 1) Random baseline

python scripts/run\_medqa\_random.py --split validation --n 1272



Purpose:

\- Sanity check for data loading and evaluation pipeline



\### 2) Encoder baseline (bi-encoder)

python scripts/run\_medqa\_encoder.py --model intfloat/e5-base-v2 --split validation --n 1272



Notes:

\- Uses cosine similarity between question and answer embeddings

\- Serves as a fast, non-generative baseline



\### 3) Small generative LLM baseline (logit-choice)

python scripts/run\_medqa\_llm.py --model microsoft/phi-2 --split validation --n 200



Notes:

\- Scores next-token logits for answer choices

\- Avoids output parsing errors

\- n=200 used for quick validation



\## Results

\- Output files are saved under results/

\- JSON files include model name, split, and accuracy

\- Result files are excluded from git via .gitignore



\## Planned experiments

\- HealthBench evaluation with open-ended generation

\- Expanded model coverage (1–7B open-weight LLMs)

\- Compositional inference strategies



