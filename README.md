# FIRE 2026 — LLM as a Judge?: From Statute Prediction to Sycophancy Detection in Law

Website for the FIRE 2026 shared track on evaluating LLMs in legal reasoning and sycophancy detection.

## Track Overview

This track provides a testbed for evaluating the efficacy of LLMs in generating trustworthy and robust solutions to important legal problems. It consists of two tasks:

### Task 1: Explainable Statute Prediction (ESP)

Given the factual description of an Indian Supreme Court case, participants must:

1. Identify which sections of the Indian Penal Code (IPC) are applicable
2. Locate the exact sentence(s) from the case facts that trigger each applicable section
3. Explain the legal reasoning connecting each fact sentence to the applicable IPC section

**Data:** 525 training cases (JSONL), 105 test cases  
**Evaluation:** Macro-F1, Micro-F1, Accuracy, ROUGE-L, BLEU, METEOR — equally weighted; Total is their arithmetic mean

### Task 2: Sycophancy Detection

Detect sycophantic behavior in LLMs — the tendency to echo user beliefs regardless of truth. Given a legal query with clear outcome expectations, participants predict whether the model will agree or disagree with the user.

**Data:** Cross-jurisdictional dataset spanning U.S. and Indian Supreme Court cases  
**Evaluation:** Accuracy, Precision, Recall, F1 (sycophantic class), Macro-F1 — ranked by Macro-F1

## Final Results

The final evaluation results are published at
[`pages/results.html`](pages/results.html) — the authoritative source for
track rankings. Top three per task:

**Task 1 — Explainable Statute Prediction** (Total = arithmetic mean of
Macro-F1, Micro-F1, Accuracy, ROUGE-L, BLEU, METEOR, equally weighted)

| Rank | Team | Best Run | Total |
|---:|---|---|---:|
| 1 | KLH | Run 2 | 0.48215 |
| 2 | DwaipayanDatta | Run 2 | 0.4330 |
| 3 | AnastasiiaPotiagalova | Run 1 | 0.3865 |

**Task 2 — Sycophancy Detection** (ranked by Macro-F1)

| Rank | Team | Best Run | Macro-F1 |
|---:|---|---|---:|
| 1 | AnastasiiaPotiagalova | Run 1 | 81.29% |
| 2 | RadhikaBohra | Run 2 | 76.81% |
| 3 | SupriyaChanda | Run 2 | 65.04% |

17 teams were ranked in Task 1 and 8 in Task 2. Results are final; no
further submissions or corrections are accepted. Working Notes are due
**15 September 2026** via [Microsoft CMT](https://cmt3.research.microsoft.com/FIRE2026)
— select the **SYCOLEX** track during submission, and do not include your
rank in the paper.

## Timeline

| Date | Milestone |
|------|-----------|
| ~~15 May 2026~~ → **20 May 2026** | Track website opens, training data released |
| ~~15 June 2026~~ → **20 June 2026** | Training data release (525 cases) |
| ~~20 July 2026~~ → **25 July 2026** | Test data release (100 cases) |
| ~~30 June 2026~~ → **5 August 2026** | Run submission deadline |
| ~~20 August 2026~~ → **31 August 2026** | Track results declared |
| ~~4 September 2026~~ → **15 September 2026** | Working notes due |
| ~~30 September 2026~~ → **5 October 2026** | Camera-ready copies |
| December 2026 | FIRE 2026 Conference |

## Organizers

- **Kripabandhu Ghosh** — IISER Kolkata, India
- **Liana Ermakova** — Université de Bretagne Occidentale, France
- **Shuvam Banerji Seal** — IISER Kolkata, India
- **Subinay Adhikary** — IISER Kolkata, India
- **Jaap Kamps** — University of Amsterdam, Netherlands

## Website Structure

```
├── index.html              # Landing page with loader, hero, tasks, timeline
├── 404.html                # Custom 404
├── pages/
│   ├── task1.html          # Task 1: ESP full specification
│   ├── task2.html          # Task 2: Sycophancy full specification
│   ├── results.html        # Final leaderboards for both tasks
│   ├── faq.html            # Frequently asked questions
│   ├── organizers.html     # Organizer details and prior experience
│   └── registration.html   # Registration information
├── css/                    # Modular CSS (base, type, components, results, etc.)
├── js/                     # Modular JS (nav, scroll-reveal, timeline, theme, etc.)
├── assets/                 # Logos, favicons, Codabench task copy
├── final_task1_data/       # Released Task 1 training set (525 cases, JSONL)
├── codabench_file/         # Task briefs as uploaded to Codabench
└── utils/pretext/          # Pretext library (git submodule)
```

See `design.md` for the full design system and file map.

## Features

- Light/dark theme with coffee-paper texture in light mode
- Sycophancy loader animation (session-cookie gated)
- Dynamic timeline with today marker and countdown
- Responsive design with mobile navigation
- Pretext-powered dynamic font resizing
- JSON syntax highlighting with typewriter animation
- Scroll-triggered reveal animations

## Local Development

```bash
# Start a local server
python3 -m http.server 8080

# Open in browser
open http://localhost:8080
```

No build step required — pure HTML/CSS/JS.

## Contact

For questions about the track, contact the organizers via email listed on the [organizers page](pages/organizers.html).
