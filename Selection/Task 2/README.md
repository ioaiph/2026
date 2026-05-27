# IOAI Philippines Selection Task 2 - Holy Week Maritime Reconnaissance

### 1. Concept & Institutional Context
Task 2 of the IOAI Philippines Selection simulates a high-stakes maritime safety operation during the Holy Week peak travel season. The scenario involves the **Philippine Coast Guard (PCG)** deploying aerial drone reconnaissance to assist **Local Government Units (LGUs)** in monitoring coastal safety. Candidates must develop a vision pipeline capable of processing these feeds to ensure public safety and identify high-priority anomalies.

### 2. Pedagogical Objective
The task evaluates a candidate’s ability to move beyond traditional supervised learning. While standard object detection is a baseline, the "win condition" requires identifying Out-of-Distribution (OOD) anomalies that do not exist in the provided training data. Success demonstrates mastery of:
* **Synthetic Data Generation:** Using Diffusion models to create training samples of rare objects in maritime environments.
* **Vision-Language Models (VLM):** Leveraging zero-shot architectures (e.g., CLIP) to identify objects based on natural language descriptions.

### 3. Classification Schema
The dataset comprises five distinct classes. The anomalies (Classes 8 & 9) are entirely absent from the training set, requiring innovative AI approaches:
* **Standard Classes:** `0: Swimmer`, `1: Boat`, `2: Debris`
* **Anomaly Classes:** `8: Soggy Bunny`, `9: Painted Egg`

### 4. Evaluation & Scoring Methodology
A **Custom Blended Metric (50/50)** has been implemented to ensure rigorous results:

| Component | Weight | Metric | Purpose |
| :--- | :--- | :--- | :--- |
| **Maritime Detection** | 50% | mAP (IoU @ 0.5) | Tests localization of standard maritime objects. |
| **Anomaly Identification** | 50% | Categorical Accuracy | Tests the identification of OOD anomalies. |

**The Ghost Box Protocol:** To reconcile image-level anomaly detection within an object-detection framework, candidates must provide a **1-pixel "Ghost Box"** at the origin `(0, 0, 1, 1)` for any detected anomaly.

### 5. Integrity & Reproducibility Guardrails
* **Kaggle-Enforced Pipeline:** Scores are only valid if generated via a successful Kaggle Notebook execution. External CSV uploads are prohibited.
* **Data Split:** A **27% Public / 73% Private** split prevents leaderboard "probing" and rewards generalizable models.
* **Audit Requirement:** **All** participant notebooks must be documented and shared. If a notebook cannot reproduce the leaderboard score or shows evidence of manual coordinate entry, the entry is disqualified.

### 6. Summary
By aligning the task with the operational needs of the PCG and LGUs, this competition identifies talent capable of building resilient, deployable AI systems that can handle the unpredictable nature of real-world national security and safety missions.