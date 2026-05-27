# IOAI Philippines Selection Task 3 - Katotohanan

Katotohanan: Filipino Fake News Classifier

**Contributed by:**
Dr. Charibeth K. Cheng
Associate Dean and Professor
College of Computer Studies
De La Salle University - Manila
### Summary
Aligned with the official International Olympiad in Artificial Intelligence (IOAI) Individual Scientific Contest format, this challenge evaluates candidates on Natural Language Processing (NLP), prompt engineering, programmatic API integration, and responsible AI and ethical reasoning. Operating under a zero-budget constraint, you must build a content moderation pipeline for Philippine online news using free-tier Large Language Models (LLMs).
### The Problem
The Philippines consistently ranks among the world's most active social media populations. During elections, disasters, and public health crises, fabricated news in Filipino and Taglish circulates at scale. Your goal is to build an automated AI pipeline that ingests raw news articles and classifies them across multiple dimensions: veracity, manipulation techniques, vulnerable targets, and ethical risk.
### The Pipeline
Your Python script must execute the following workflow:
* **Data Ingestion:** Load the dataset from the Kaggle input directory.
* **LLM Integration:** Iterate through articles and query a free-tier API (e.g., OpenRouter, Groq, or Gemini).
* **Prompt Engineering:** Use few-shot prompting to accurately parse Philippine code-switching and idioms.
* **Strict Formatting:** Enforce JSON output with no conversational filler to ensure programmatic parsing.
* **Error Handling:** Implement try/except backoff logic to manage API rate limits and connection timeouts.
### The Scientific Contest
This task requires translating messy, culturally-grounded natural language into a strict machine-readable schema. 
* **Linguistic Equity:** Performance on regional languages like Cebuano, Ilocano, and Waray is weighted heavily in the final evaluation.
* **The Anti-Lookup Rule:** The use of source-level mapping tables or hard-coded "cheat sheets" is strictly prohibited. Your model must classify an article based on its content, tone, and rhetorical features.

---

# The Dataset

### Philippine Fake News Corpus
This competition uses a comprehensive collection of 22,458 raw news articles from various Philippine media landscapes.
* **Credible Sources:** 14,802 articles from mainstream broadsheets including the Inquirer, Manila Bulletin, and Manila Times.
* **Not-Credible Sources:** 7,656 articles from outlets cited as unreliable or satire sources by established monitoring groups.

### Source-Level Mapping
Ground-truth labels for the leaderboard are derived from the source website and its historical classification:

| Source(s) | Manipulation Type | Description |
| :--- | :--- | :--- |
| Adobo Chronicles | Satire-as-fact | Self-described satire mixing facts with fabricated quotes. |
| Get Real Philippines, GR Pundit | Opinion-as-fact | Editorial opinion presented as straight reporting. |
| Thinking Pinoy, Duterte Today | Politically-motivated fabrication | Documented cases of fabricated quotes and events. |
| VerifiedPH, Pinoy Trending News | Misleading-headline | Sensationalized or false headlines attached to real content. |
| Pinoy News Blogger, etc. | Fabricated | Content with no basis in verifiable events or reporting. |
| Inquirer, Bulletin, Times | Authentic | Mainstream credible broadsheets. |

### Dataset Details
* **Timeline:** Articles range from January 1, 2016, to October 31, 2018.
* **Languages:** Includes Filipino, Taglish, and regional languages.
* **Format:** Every record is real, sourced content with no synthetic augmentation.
* **Dataset Access:** https://huggingface.co/datasets/SEACrowd/ph_fake_news_corpus
* **GitHub (Original):** https://github.com/aaroncarlfernandez/Philippine-Fake-News-Corpus
* **Original Work:** Fernandez, A.C. (2018). Computing the Linguistic-Based Cues of Fake News in the Philippines Towards its Detection. Master's Thesis. Mapua University.

### Files
* **test.csv:** The inference set containing the record index and raw article content.
* **sample_submission.csv:** A template showing the required 134,748-row submission format.

---

# # Evaluation Criteria

### The Output Schema
Your pipeline must extract six distinct labels for every record in the test set. These fields are designed to capture both the veracity of the information and the ethical risk associated with it.

| Field | Values / Description |
| :--- | :--- |
| **veracity** | Fake, Real |
| **manipulation_type** | Fabricated, Satire-as-fact, Opinion-as-fact, Misleading-headline, Politically-motivated fabrication, Authentic |
| **target_group** | Disaster-victim, Political-figure, Ethnic-minority, Religious-group, None |
| **confidence_score** | A float between 0.0 and 1.0 |
| **harm_level** | High, Medium, Low, None |
| **needs_fact_check** | Yes, No |

### Ethical Dimensions
The following categories are evaluated via manual review of your prompts and code. They represent the "Responsible AI" component of the challenge:

| Dimension | Role in Content Moderation |
| :--- | :--- |
| **Linguistic Equity** | Measures model performance on regional languages (Cebuano, Ilocano, Waray) to prevent "Metropolitan Bias." |
| **Target Group Identification** | Identifies whether the disinformation specifically targets vulnerable populations or public figures. |
| **Harm Level Analysis** | Determines the potential real-world consequences (e.g., physical danger, social unrest) of the narrative. |
| **The Confidence Trap** | Evaluates Expected Calibration Error (ECE) to ensure models are not "confidently wrong" during crises. |
| **Fact-Check Triaging** | Flags content that requires immediate human intervention based on urgency and risk. |

### Submission Format
Final output must be a UTF-8 encoded CSV with exactly **134,748 rows**. Each article in the test set requires six rows in the submission file, identified by a composite key.
* **RowId:** `[index]_[label_name]` (e.g., `104_veracity`, `104_harm_level`).
* **Prediction:** The predicted value for that specific label.

### Metrics and Scoring
1. **Kaggle Leaderboard (10%):** Calculated via Relative Normalization of the Macro F1-Score for Veracity and Manipulation Type.
2. **Calibration Score (5%):** Evaluated via Expected Calibration Error (ECE).
3. **Ethical & Linguistic Logic (5%):** Manual review of how your model handles the Ethical Dimensions listed above.
4. **Engineering Rigor (5%):** Manual review of your pipeline’s efficiency and error handling.

---
# Scoring Rubrics

**Component Weight:** 25% of Total Grade  
**Competition Period:** April 6 – April 13, 2026

---

## 1. Scoring Architecture
Task 3 is evaluated across four distinct pillars. This selection process prioritizes **Scientific Rigor**, **Linguistic Equity**, and **Ethical Calibration** over raw accuracy alone.

| Category | Weight | Evaluation Method |
| :--- | :--- | :--- |
| **Kaggle Performance** | 10% | Relative Normalization (Macro F1) |
| **Calibration (ECE)** | 5% | Automated Calculation from Submission CSV |
| **Ethical & Linguistic Logic** | 5% | Manual Review of System Prompts & Reasoning |
| **Engineering & Resource Mgmt** | 5% | Manual Review of Python Pipeline & Efficiency |

---

## 2. Performance Standards (0-5 Scale)

### Pillar A: Kaggle Performance (10%)
To account for the inherent difficulty of the dataset and ensure fairness across the cohort, this component uses **Relative Normalization** based on the Macro F1-score.

**Calculation:** `Points = 10 * (Candidate Macro F1 / Top Candidate Macro F1)`

* The top-performing candidate automatically receives the full **10.0 points**.
* All other candidates receive points proportional to their performance relative to the leader.
* **Zero Credit:** Evidence of manual labeling, use of prohibited lookup tables, or failure to submit results in the correct format.

### Pillar B: Calibration & Uncertainty (5%)
Evaluates the Expected Calibration Error (ECE), measuring how well your `confidence_score` reflects actual accuracy.

* **5 (Elite):** ECE < 0.1. The model is highly self-aware of its own limitations.
* **4 (Strong):** ECE 0.1 – 0.2. Generally well-calibrated with minor over/under-confidence.
* **3 (Functional):** ECE 0.2 – 0.4. The model is frequently overconfident in its incorrect predictions.
* **2 (Poor):** ECE > 0.4. The confidence scores have little to no correlation with actual accuracy.
* **1 (Static):** Uses a uniform confidence score for all entries (e.g., all 1.0) to bypass the metric.
* **0 (No Credit):** Confidence scores are missing, randomized, or malformed.

### Pillar C: Ethical & Linguistic Logic (5%)
Manual review of the system prompts and the logic used for `harm_level`, `target_group`, and `needs_fact_check`.

* **5 (Pro-Level):** Prompts demonstrate deep reasoning about Philippine code-switching and regional languages (Cebuano, Ilocano, Waray).
* **4 (Nuanced):** Clear logic for identifying vulnerable groups; captures Taglish well but misses some regional context.
* **3 (Functional):** Basic prompt engineering relying on standard LLM defaults.
* **2 (Surface-Level):** Generic prompts using simple keyword triggers rather than contextual understanding.
* **1 (Incoherent):** Prompts are poorly structured or fail to address the 6-label schema.

### Pillar D: Engineering & Resource Management (5%)
Evaluates the ability to manage the 22,458-article loop under "Zero-Budget" and rate-limit constraints.

* **5 (Production Grade):** Sophisticated exponential backoff/retry logic; flawless handling of the full dataset on free-tier APIs.
* **4 (Robust):** Effective rate-limit management; code is readable, modular, and reproducible.
* **3 (Sufficient):** Basic error handling; script successfully finishes the task.
* **2 (Fragile):** Minimal error handling; script likely crashes on common API timeouts or JSON parsing errors.
* **1 (Incoherent):** Unreadable code or hard-coded paths/API keys.

---

## 3. Mandatory Deductions (Red Flags)
The following violations trigger automatic point deductions from your Task 3 total:

1. **The Anti-Lookup Penalty (-5 Points):** Hard-coded mapping of source names or URLs to labels (e.g., `if source == "Adobo Chronicles" then label = "Satire"`).
2. **The Overconfidence Penalty (-2 Points):** More than 90% of your `confidence_score` entries are exactly 1.0.
3. **The Regional Erasure Penalty (-1 Point):** Prompt or code explicitly ignores the regional language requirements (Cebuano, Ilocano, Waray).

---

# Competition Rules

### 1. Account and Team Integrity
* **Individual Participation:** This is an individual scientific contest. You may only participate using a single Kaggle account. 
* **No Private Sharing:** Privately sharing code, prompts, or data "cheat sheets" between candidates is strictly prohibited. All work must be your own original engineering.
### 2. Submission Limits
* **Daily Limit:** You are permitted a maximum of **2 submissions per day**. 
* **UTC Reset:** Note that the Kaggle daily reset occurs at 00:00 UTC. 
* **Final Selection:** You must manually select **1 submission** to be evaluated against the Private Leaderboard. 
### 3. Scientific Constraints (The "Zero-Budget" Rule)
* **API Usage:** You are restricted to **free-tier LLM APIs** (e.g., Gemini Flash, Groq, OpenRouter free models). The use of paid API credits or "Pro" tiers is prohibited.
* **Anti-Lookup Rule:** Your model must classify articles based on linguistic and rhetorical content. Hard-coding labels based on news source names or URLs is strictly forbidden.
### 4. Technical Submission Requirements
* **Kaggle Notebooks:** All work must be performed and submitted via a Kaggle Notebook. 
* **"Submit to Competition" Feature:** You must use the official "Submit to Competition" button within your notebook to generate your leaderboard score.
* **Visibility:** Your final notebook must be shared with the competition organizers before the deadline.
### 5. Documentation and Reporting
* **No Separate Submissions:** All documentation, ethical reasoning, and technical reports must be written as Markdown cells **within the notebook itself**. 
* **Contents:** The notebook must include the final code, the resulting scores, and the documentation for your pipeline and prompts. External PDFs or document links will not be accepted.
### 6. Timeline (All times in PHT)
* **Competition Start:** April 6, 2026, 12:00 AM PHT
* **Final Deadline:** April 13, 2026, 11:59 PM PHT
* **Notebook Sharing Deadline:** April 13, 2026, 11:59 PM PHT (Simultaneous with competition close)