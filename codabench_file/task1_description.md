# Task 1: Explainable Statute Prediction (ESP)

## Overview

Given the factual description of an Indian Supreme Court case, participants must:

1. **Identify** which sections of the Indian Penal Code (IPC) are applicable
2. **Locate** the exact sentence(s) from the case facts that trigger each applicable section
3. **Explain** the legal reasoning connecting each fact sentence to the applicable IPC section

This task tests both **legal knowledge** (which sections apply?) and **interpretability** (why do they apply, grounded in the facts?).

## Jurisdiction & Scope

| Included | Not Included |
|---|---|
| Indian Supreme Court only | Bharatiya Nyaya Sanhita (BNS) |
| Indian Penal Code (IPC) sections | CrPC, Evidence Act |
| — | U.S. statutes |

**Legal categories:** Criminal, Civil, Constitutional, Tax, Labor, Commercial, Revenue, Administration, Environmental

## Training Data

| Statistic | Value |
|---|---|
| Release date | 20 June 2026 |
| Cases | 525 |
| Format | JSONL (one JSON object per line) |
| Avg. fact length | ~2,583 chars |
| IPC sections covered | 7 (147, 201, 302, 376, 420, 498A, 506) |

Each line in the training set has the following structure:

```json
{
  "doc_id": "2013.INSC.228.txt",
  "fact": "Full case factual description...",
  "explanation": {
    "The facts which are essential to be stated for adjudication...": "IPC 147",
    "on 1992, on hearing a gunshot sound and...": "IPC 147"
  },
  "statute": ["IPC 147"]
}
```

| Field | Type | Description |
|---|---|---|
| `doc_id` | string | Unique case identifier (e.g., `"2013.INSC.228.txt"`) |
| `fact` | string | Full factual description of the case (~2,583 chars average) |
| `explanation` | dict | Sentence-to-statute mapping. Each key is a sentence from the fact; each value is the IPC section code that sentence supports |
| `statute` | list[string] | List of IPC section codes applicable to the case (e.g., `["IPC 302", "IPC 201"]`) |

### IPC Section Codes

| Code | Section | Description |
|---|---|---|
| `IPC 147` | Section 147 IPC | Punishment for rioting |
| `IPC 201` | Section 201 IPC | Causing disappearance of evidence |
| `IPC 302` | Section 302 IPC | Punishment for murder |
| `IPC 376` | Section 376 IPC | Punishment for rape |
| `IPC 420` | Section 420 IPC | Cheating and dishonestly inducing delivery of property |
| `IPC 498A` | Section 498A IPC | Cruelty by husband or relative of husband |
| `IPC 506` | Section 506 IPC | Punishment for criminal intimidation |

A single case may have multiple statute entries (one per applicable IPC section). The `explanation` field maps each sentence in the fact to the specific IPC section it supports. Multiple sentences may map to the same statute.

## Test Data

| Statistic | Value |
|---|---|
| Release date | 25 July 2026 |
| Cases | 105 |
| Format | JSONL |

The test data provides only the input — no labels:

```json
{
  "doc_id": "2002.INSC.274.txt",
  "fact": "Full case factual description..."
}
```

Participants must predict **all three outputs**: section labels, exact_fact sentences, and reasoning traces.

## Submission Format

Participants submit a single JSONL file with one line per test case:

```json
{
  "doc_id": "2002.INSC.274.txt",
  "statute": [
    {
      "section": "IPC 376",
      "exact_fact": "She recognized the respondent Kishanlal and asked him as to why he had come. He said that he had come to have sexual intercourse with her...",
      "reasoning_trace": "Section 376 IPC applies because the facts establish that the respondent committed sexual intercourse with the prosecutrix against her will, satisfying the ingredients of rape under Section 375 IPC."
    },
    {
      "section": "IPC 457",
      "exact_fact": "While going to Ramlila her husband had bolted the house from outside. At about 11-12 O' clock at night she woke up as someone opened the door.",
      "reasoning_trace": "Section 457 IPC applies because the respondent entered the house as a trespasser with intent to commit an offence, having opened the bolted door to gain entry at night."
    }
  ]
}
```

### Submission rules

- Single run per team
- No team size limit
- JSONL format only, one line per test case
- Each line must contain `doc_id` and `statute` (list of predictions)
- Each `statute` entry must contain `section`, `exact_fact`, and `reasoning_trace`

### Note on `exact_fact` and `reasoning_trace`

- `exact_fact`: The sentence(s) from the case fact that trigger the applicable section. Must be a direct quote from the fact text.
- `reasoning_trace`: The legal reasoning connecting the fact sentence(s) to the IPC section. This is a free-text explanation of why the section applies, grounded in the facts.

The `explanation` field in the training data provides a sentence-to-statute mapping that can be used to construct the `exact_fact` and `reasoning_trace` fields.

## Evaluation

Metrics and weights are **tentative** and may be updated before the test data release.

| Metric | Weight | Description |
|---|---|---|
| **Macro F1** | 35% | Exact match on predicted section labels vs. gold standard |
| **ROUGE-L** | 25% | Longest common subsequence similarity between participant's reasoning and gold reasoning |
| **BLEU** | 20% | Sentence-level BLEU score between reasoning texts |
| **Recall@3** | 10% | Whether gold section labels appear in the participant's top-3 predictions |
| **Legal Semantic Score (LSS)** | 10% | Cosine similarity of reasoning embeddings from an undisclosed legal-domain language model |

**Composite Score** = weighted sum of above metrics.

Evaluation is conducted on **CodaBench** (CodaLab v2). The scoring script is released with the test data. The leaderboard updates automatically after each submission.

### Legal Semantic Score

The **Legal Semantic Score** uses a pre-trained legal-domain embedding model. The specific model will **NOT** be disclosed to participants, preventing gaming of this metric.

## Baselines

At least one baseline system will be provided to participants. Potential baselines:

| Baseline | Description |
|---|---|
| **Zero-shot LLM** | Prompt with facts only — no examples provided |
| **Few-shot LLM** | 5 examples in prompt for in-context learning |
| **BERT Classifier** | Fine-tuned BERT-based model trained on the training set |

## Timeline

| Date | Milestone |
|---|---|
| ~~15 May 2026~~ → **20 May 2026** | Track website opens, training data released |
| ~~15 June 2026~~ → **20 June 2026** | Training data release (525 cases) |
| ~~20 July 2026~~ → **25 July 2026** | Test data release (105 cases) |
| ~~30 June 2026~~ → **5 August 2026** | Run submission deadline |
| ~~15 July 2026~~ → **20 August 2026** | Track results declared |
| ~~30 August 2026~~ → **4 September 2026** | Working notes due |
| ~~30 September 2026~~ → **5 October 2026** | Camera-ready copies |
| **December 2026** | FIRE 2026 Conference |

## Ethical Considerations

- All case data is from **publicly available** Indian Supreme Court judgments
- No personally identifiable information is included
- The task is designed to advance legal AI interpretability, **not to provide legal advice**