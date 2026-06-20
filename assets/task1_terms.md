# Task 1: Explainable Statute Prediction — Terms of Participation

By registering for and participating in Task 1 (Explainable Statute Prediction), you agree to the following terms and conditions.

---

## 1. Data Usage

1.1. The training data, test data, and any materials provided through this shared task are licensed under the **Creative Commons Attribution 4.0 International License (CC-BY-4.0)**.

1.2. You may share, adapt, and build upon the data for any purpose, including commercially, provided you give appropriate credit to the organizers and include a reference to this shared task.

1.3. Attribution must include:
- The task title: *"Task 1: Explainable Statute Prediction (ESP)"*
- The shared track title: *"LLM as a Judge?: From Statute Prediction to Sycophancy Detection in Law"*
- The conference: *"FIRE 2026 (Forum for Information Retrieval and Evaluation)"*
- A link to the task website: `https://sycolex.com/pages/task1.html`

## 2. Data Source and Provenance

2.1. All case data is derived from **publicly available Indian Supreme Court judgments** sourced from the [LII of India](http://www.liiofindia.org/).

2.2. The data does not contain any personally identifiable information (PII). Case facts are summaries of judicial proceedings; no names or details of private individuals beyond what is contained in the published judgments are included.

2.3. The data is provided **as-is**. The organizers make no warranty as to the completeness, accuracy, or fitness of the data for any particular purpose.

## 3. Permitted Use

3.1. The data may be used solely for the purpose of participating in this shared task, for academic research related to this task, and for writing task reports or working notes.

3.2. Participants may develop and publish models, methods, and analyses based on the training data. Any publication must cite the task and acknowledge the data source.

3.3. Participants may share their trained models and predictions with other researchers, subject to the CC-BY-4.0 license.

## 4. Prohibited Use

4.1. **Do not use the data to provide legal advice, legal services, or to make legal judgments about real cases.** The data is provided for research purposes only and does not constitute legal information or legal advice.

4.2. **Do not attempt to re-identify the full source judgment texts** from the provided fact excerpts. The fact summaries are provided for research purposes; matching them to the original judgments is not required and should be avoided.

4.3. **Do not use the data to train commercial legal-advice systems** without explicit written permission from the organizers.

4.4. **Do not redistribute the test data or test labels** during the evaluation period, except through the official CodaBench mechanism.

## 5. Submission Rules

5.1. Each team may submit **one run per task** during the evaluation phase.

5.2. Teams may consist of any number of participants. There is no team size limit.

5.3. Submissions must conform to the format described in the task page. Submissions that do not conform may be discarded without notice.

5.4. All members of a team must be affiliated with an academic institution, research organization, or industry lab at the time of submission.

5.5. Submissions must be the original work of the team. Plagiarism, unauthorized use of other teams' work, or any form of academic dishonesty will result in disqualification.

## 6. Evaluation and Scoring

6.1. Evaluation will be conducted on **CodaBench** (CodaLab v2). The scoring script will be released alongside the test data.

6.2. The composite score is computed as a weighted sum of the following metrics (tentative, subject to update):

| Metric | Weight |
|---|---|
| Macro F1 | 35% |
| ROUGE-L | 25% |
| BLEU | 20% |
| Recall@3 | 10% |
| Legal Semantic Score | 10% |

6.3. The **Legal Semantic Score** uses an undisclosed legal-domain embedding model. The specific model will not be released to prevent metric gaming. By participating, you accept the use of this opaque metric.

6.4. The leaderboard is ranked by **Composite Score** (weighted sum). The organizers reserve the right to adjust metric weights before the final evaluation; such adjustments will be announced at least 48 hours before the evaluation deadline.

6.5. The organizers reserve the right to disqualify any team that violates the terms of participation, engages in gaming behavior (e.g., overfitting to the evaluation metric without genuine model development), or acts in bad faith.

## 7. Intellectual Property

7.1. Participants retain full ownership of their models, code, and any works they produce using the data.

7.2. By submitting a run, participants grant the organizers a non-exclusive license to use their submission for the purposes of running the shared task, computing the leaderboard, and producing task results. Participants retain the right to publish their methods independently.

7.3. Working notes (post-task analysis papers) will be published as part of the FIRE 2026 proceedings. By submitting a working note, participants grant the organizers a license to publish it.

## 8. Privacy

8.1. Participant names and affiliations will be displayed on the public leaderboard unless the team requests anonymity.

8.2. The organizers will not share participant contact information with third parties without consent.

8.3. The organizers will retain submission data for the purpose of generating the task results and may retain it after the task concludes for statistical analysis and quality assurance.

## 9. Disclaimer

9.1. The organizers, affiliated institutions, and the FIRE 2026 conference assume no liability for any damages arising from the use of the data or participation in the task.

9.2. The data and task results are provided for research purposes only and should not be used for any consequential or real-world application without independent verification.

9.3. Nothing in these terms or the task materials constitutes legal advice, medical advice, or any other form of professional advice.

## 10. Changes to Terms

10.1. The organizers reserve the right to update these terms at any time. Material changes will be announced on the task website and on CodaBench at least 48 hours before taking effect.

10.2. Continued participation after the effective date of any changes constitutes acceptance of the updated terms.

## 11. Contact

For questions about these terms, the task, or participation, please contact:

- **Kripabandhu Ghosh** — [kripaghosh@iiserkol.ac.in](mailto:kripaghosh@iiserkol.ac.in) (IISER Kolkata)
- **Shuvam Banerji Seal** — [sbs22ms076@iiserkol.ac.in](mailto:sbs22ms076@iiserkol.ac.in) (IISER Kolkata)
- **Liana Ermakova** — [liana.ermakova@univ-brest.fr](mailto:liana.ermakova@univ-brest.fr) (Université de Bretagne Occidentale)
- **Subinay Adhikary** — [sa21rs094@iiserkol.ac.in](mailto:sa21rs094@iiserkol.ac.in) (IISER Kolkata)
- **Jaap Kamps** — [kamps@uva.nl](mailto:kamps@uva.nl) (University of Amsterdam)

---

*Last updated: 20 June 2026*
*CC-BY-4.0: https://creativecommons.org/licenses/by/4.0/*
