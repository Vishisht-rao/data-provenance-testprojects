# Movie Review Sentiment: LLM Eval Task

## Task

Run an LLM eval on the movie reviews in this folder with each of the three prompt variations in `prompts.py`. The wider goal is to see whether changing the prompt shifts the distribution of output labels.

**Your task is only to run the LLM evals.** Run every prompt on every review for each of the three models specified below, and save the model's responses. Analysis of the label distribution is not a part of this task. The model's responses and corresponding receipts will be the final deliverables.

## Models
Run this task on the following 3 models: anthropic/claude-sonnet-5, openai/gpt-6-sol, google/gemini-3.8-flash.

## Prompts

`prompts.py` contains a list of three prompt strings. Each one asks the model to label a review as exactly `positive` or `negative`, and to return only the label. The variations differ in how the model should weigh the review:

1. Neutral: judge the review as a whole.
2. Leaning negative: pay particular attention to criticism, and prefer `negative` when there is substantial negative sentiment.
3. Leaning positive: pay particular attention to praise, and prefer `positive` when there is substantial positive sentiment.

Each review gets each prompt once: 200 reviews × 3 prompts x 3 models = 1800 model calls.

## Dataset

The dataset can be downloaded here: 

There are 200 movie reviews stored as plain-text `.txt` files, 100 per sentiment class. Each folder name is the review's ground-truth sentiment. The files keep their original names from the source dataset, for example `cv000_29590.txt`.

| Folder | Sentiment | Number of files |
|---|---|---:|
| positive | Positive | 100 |
| negative | Negative | 100 |
| **Total** | | **200** |

- The reviews were sampled at random (seed 42) from the Cornell Movie Review Data, *polarity dataset v2.0* (Pang & Lee, 2004), which has 1,000 positive and 1,000 negative reviews. The text is unchanged: it is already lowercased and tokenized, as in the original dataset.
