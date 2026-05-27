# IOAI Philippines Selection Task 1 - The "Bayanihan" Crisis Concept Extractor

## 1. Executive Summary
To align with the official IOAI Individual Scientific Contest format, this technical challenge evaluates candidates on Natural Language Processing (NLP), Automatic Speech Recognition (ASR), prompt engineering, and programmatic API integration. Operating under a zero-budget constraint, this task simulates real-world, multi-modal data extraction using free-tier Large Language Models (LLMs), local transcription models, and Kaggle's automated evaluation infrastructure.
## 2. The Core Problem
During severe weather events, local rescue organizations receive thousands of unstructured, chaotic distress signals. The challenge is to build an automated AI pipeline that ingests raw, abbreviated Taglish SMS texts alongside static-filled radio audio intercepts, and extracts critical, structured data for emergency triage.

This mirrors the IOAI "Concepts" tasks by forcing students to translate messy human context and noisy audio into strict, machine-readable formats.
## 3. Task Mechanics
* **The Input:** Candidates receive a dataset of 10,000 synthetic Taglish disaster SMS messages and a critical subset of 50 shortwave radio audio intercepts (`.mp3` files). The text data includes extreme abbreviations, local slang, and a portion of "noise" (e.g., spam, wrong numbers). The audio data features dispatcher 10-codes over heavy background static.
* **The Pipeline:** Candidates must write a Python script that programmatically transcribes the audio files (e.g., using Whisper), iterates through the dataset, queries a free-tier LLM API (e.g., OpenRouter, Groq), and parses the multimodal text.
* **The Output:** The script must extract four distinct labels per record:
    * `urgency_level`: Categorical (Critical, High, Moderate, Non-Emergency)
    * `location`: Extracted string (or "Unknown")
    * `needs_rescue`: Binary (Yes or No)
    * `needs_medical`: Binary (Yes or No)
* **The Submission Format:** To evaluate all four categories simultaneously, the final output must be a "melted" (flattened) CSV file consisting of exactly 40,000 rows with two columns: `RowId` (e.g., `1_urgency_level`) and `Prediction`.
## 4. Evaluation & Infrastructure
* **Platform:** Hosted entirely via a private Kaggle Community Competition.
* **Evaluation Metric:** **Macro F1-Score**. This standard metric balances precision (penalizing hallucinated emergencies) and recall (penalizing missed distress calls), averaged across all submitted categories in the melted format.
* **Anti-Cheating Mechanism:** The 40,000-prediction volume makes manual, human-driven labeling impossible within the timeframe, forcing true algorithmic automation.
## 5. Key Competencies Tested
* **Multi-Modal AI Pipelines:** Integrating local models (like Whisper for ASR) with cloud-based LLM APIs to process both audio and text in a single loop.
* **API & Infrastructure Wrangling:** Managing API keys securely via Kaggle Secrets, handling HTTP requests, and programming rate-limit fallbacks (e.g., try/except backoffs).
* **Contextual Prompt Engineering:** Using Few-Shot prompting to teach base models to accurately parse Philippine code-switching, idioms, and 10-codes.
* **Strict Schema Enforcement:** Forcing an LLM to output valid, parseable formats (like strict JSON) without conversational filler.
## 6. Competition Rules & Anti-Cheating Policy
1.  **Code Requirement:** To qualify for the next round and be considered for the National Team, participants must make their Kaggle Notebooks public or share them directly with the organizers immediately after the competition deadline.
2.  **Programmatic Execution:** All audio transcriptions and LLM extractions must occur programmatically during the notebook's runtime. You must use an API or load a model to process the data.
3.  **No Manual Shortcuts:** Submitting manually pre-computed transcriptions, hardcoding answers, or utilizing third-party web GUIs (like dragging files into an online transcriber) is grounds for immediate disqualification. Your code must do the work.
4.  **Official Data Paths Only:** Notebooks must exclusively load data from the official competition input directory (e.g., `/kaggle/input/`). Uploading external datasets that contain pre-computed answers, manual transcriptions, or modified audio files to bypass the programmatic execution requirement is strictly prohibited.
5.  **Individual Effort & Integrity:** As this selection phase determines the final roster of delegates, all code, prompts, and pipeline architectures must be strictly your own individual work. Collaboration, code-sharing between participants, or utilizing another candidate's API keys will result in immediate disqualification.
6.  **API Security (Kaggle Secrets):** You must never hardcode your API keys directly into your Python script. You must use the "Kaggle Secrets" feature (found under Add-ons -> Secrets in the notebook editor) to securely load your keys. Hardcoding API keys into a notebook before making it public demonstrates poor security practices and is grounds for disqualification.