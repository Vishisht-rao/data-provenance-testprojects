# arXiv Paper Classification: LLM Eval Task

## Task

Run an LLM eval on the arXiv papers in this folder with each of the three prompt variations in `prompts.py`. The wider goal is to see whether changing the prompt shifts the distribution of output labels.

**Your task is only to run the LLM evals.** Run every prompt on every paper for each of the three models specified below, and save the model's repsonses. Analysis of the label distribution is not a part of this task. The model's responses and corresponding receipts will be the final deliverables.

## Models
Run this task on the following 3 models: anthropic/claude-sonnet-5, openai/gpt-6-sol, google/gemini-3.8-flash.

## Prompts

`prompts.py` contains a list of three prompt strings. Each one asks the model to put a paper into exactly one of `cs.AI`, `math.PR`, `physics.optics` or `q-bio.NC`, and to return only the label. The variations differ in what the model should base its decision on:

1. The paper's central research topic and application area.
2. The paper's core methodology and mathematical framework.
3. The terminology and vocabulary that appear most prominently.

Each paper gets each prompt once: 100 papers x 3 prompts x 3 models = 900 model calls.

## Dataset

The dataset can be downloaded here: https://drive.google.com/drive/folders/1C7kShS5V78trfoNRNljoAEdLO8oqA_wF?usp=sharing

There are 100 arXiv papers stored as raw PDF files, 25 per category. Each folder name is the paper's primary arXiv category. Each file is named after its arXiv ID, for example `2401.01234.pdf`.

| Folder | Category | Number of files |
|---|---|---:|
| cs.AI | Artificial Intelligence | 25 |
| math.PR | Probability | 25 |
| physics.optics | Optics | 25 |
| q-bio.NC | Neurons and Cognition | 25 |
| **Total** | | **100** |

- The papers were submitted to arXiv between January and March 2024 and were found through the arXiv API. Each paper's primary category is the category of its folder, and each file is version 1 of its paper.
