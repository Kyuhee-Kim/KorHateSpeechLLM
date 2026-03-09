# Prompt Templates

This document contains the prompt templates used in the experiments.

## Placeholders

- {EVALUATION_DATASET}: the dataset of comments to be labeled
- {REFERENCE_DATASET}: the retrieval corpus used in the RAG setting
- {LABEL_DEFINITIONS}: label definition block (IDs 0–8)

## Label Definitions (used in RAG / CoT / Persona only)

- 0: Origin — Attacking, mocking, or excluding people based on region or hometown (incl. regional slurs).
- 1: Physical — Derogatory remarks about physical traits or disabilities.
- 2: Political — Attacks based on political ideology, party support, or political stance.
- 3: Profanity — General swearing or personal insults not attributable to a specific targeted hate category.
- 4: Age — Demeaning or mocking people based on age or generation.
- 5: Gender — Hate or discrimination based on gender or sexual orientation.
- 6: Race — Hate targeting race, ethnicity, skin colour, or ancestry.
- 7: Religion — Insults or hatred targeting a religion or religious group.
- 8: Not Hate Speech — Non-hate content; none of the above categories apply.

## Baseline prompt

```text
Task
Predict the label(s) for each comment in {EVALUATION_DATASET}.
Each comment may receive multi-label.

Label definitions
- 0: Origin
- 1: Physical
- 2: Political
- 3: Profanity
- 4: Age
- 5: Gender
- 6: Race
- 7: Religion
- 8: Not hate speech

**RAG prompt**

Task
Using {REFERENCE_DATASET} as a retrieval source, predict the label(s) for each comment in {EVALUATION_DATASET} among 9 labels.
Hate speech may receive multi-label.
Label 8 (not hate speech) is assigned only as a single label.

Label Definitions
{LABEL_DEFINITIONS}

**CoT prompt**

Task
Predict the label(s) for each comment in {EVALUATION_DATASET} among 9 labels.
Hate speech may receive multi-label.
Label 8 (not hate speech) is assigned only as a single label.

Decision procedure
Follow the steps below to make your decision.

Step 1. Identify the core meaning of the comment.
Step 2. Check whether it contains expressions that match any category definition.
Step 3. Consider that labels 0--7 may co-occur (multi-label).
Step 4. Select all applicable labels as the final answer.

Label Definitions
{LABEL_DEFINITIONS}

Example
Comment: If a woman had acted like Choi Soo-jong, people would have gone crazy---"Why is only the woman speaking politely? Is she some kind of servant?", "Poor thing, get a divorce.", "This is sexist TV, cancel the show.", and so on. But when a man does it, they call it "nice" and say they are a loving couple. This is exactly why I cannot help but hate those "Kimchi girls."
Final label(s): 3,5

**Persona prompt**

You are Korean and an expert in linguistics and content moderation.
Your primary role is to analyze the given text, accurately identify and classify language-based hate speech, and, when necessary, briefly explain the rationale for your decision.

You should be particularly sensitive to the following aspects:
- Explicit and implicit hate speech
- Cultural and contextual nuances
- Slurs, stereotypes, slang and coded language (euphemisms or obfuscated expressions)
- Power relations and targeted groups

Maintain a neutral, analytical, and non-judgmental stance.
Do not censor, edit, or rewrite the text.
Perform analysis and classification only.

Your goal is to minimize omissions without sacrificing precision.
If you are uncertain, explicitly state your uncertainty.

Task
Predict the label(s) for each comment in {EVALUATION_DATASET} among 9 labels.
Hate speech may receive multi-label.
Label 8 (not hate speech) is assigned only as a single label.

Label Definitions
{LABEL_DEFINITIONS}

Label Definitions
{LABEL_DEFINITIONS}
