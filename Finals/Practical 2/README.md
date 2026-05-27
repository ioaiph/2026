# IOAI Philippines 2026 National Finals - Practical 2 - The Eye of the Storm

### Can your AI estimate the destructive power of a Category 5 hurricane just by looking at its shape?

Welcome to the **National Finals** of the 2026 International Olympiad in Artificial Intelligence (IOAI) Philippines.

In the previous round, you estimated **Atmospheric Pressure** to understand the *potential* of a storm. Now, in the Finals, we shift to the metric that actually defines destruction: **Maximum Sustained Wind Speed.**

You are provided with satellite imagery of **Hurricane Beryl**, the earliest Category 5 Atlantic hurricane on record. Your mission is to train a computer vision model that can learn the visual signatures of intensification—eye formation, symmetry, and cloud density—and accurately predict the wind speeds of **Hurricane Milton**, one of the most explosive storms in history.

**The stakes are high. The physics are real. Good luck.**

---

## 🌪️ The Challenge: Estimating Intensity from Space

Meteorologists have used the **Dvorak Technique** for decades to estimate tropical cyclone intensity based on satellite patterns. However, rapid intensification cycles (where a storm jumps 30+ knots in 24 hours) remain notoriously difficult to predict.

Your task is to build a Deep Learning model that acts as an **Automated Dvorak System**. By analyzing infrared satellite imagery, your model must output the **Maximum Sustained Wind Speed (in Knots)**.

### 📂 The Dataset: A Tale of Two Monsters

This dataset focuses on two historic storms from the 2024 Atlantic Hurricane Season. Both were "Rapid Intensifiers" that reached Category 5 status, but they occurred in different months and locations.

#### **1. Training Set: Hurricane Beryl (June-July 2024)**
* **Context:** Beryl was a historic anomaly—the earliest Category 5 hurricane ever recorded in the Atlantic.
* **Data:** You are provided with **500 labeled images** covering its lifecycle from a disorganized Tropical Storm (35 knots) to a 165 mph monster (145 knots) and its eventual decay.
* **Labels:** The `train.csv` file contains the ground truth wind speeds.

#### **2. Test Set: Hurricane Milton (October 2024)**
* **Context:** Milton was an explosive storm in the Gulf of Mexico, intensifying at a rate rarely seen in history (peaking at 180 mph / 155 knots).
* **Data:** You are provided with **500 unlabeled images**.
* **Task:** You must predict the wind speed for every image in this set.

### 🚀 The Goal
Your model must learn the **universal visual features** of high-wind storms from Beryl and generalize them to Milton.

* Does your model recognize an "Eye"?
* Can it distinguish between a messy "invest" (30 knots) and a symmetric "buzzsaw" (150 knots)?
* Can it handle the "Eyewall Replacement Cycles" where the eye blurs but the storm remains dangerous?

---
### ⚠️ A Note on Integrity
**External Data is Strictly Prohibited.**
Since Hurricane Milton is a historical event, its wind speed data is publicly available online.
* **Looking up the "answers"** from the National Hurricane Center (NHC) or Wikipedia to hardcode your predictions is **CHEATING**.
* Your solution must derive its predictions **solely from the image pixel data**.
* We reserve the right to audit your code. Hardcoded values based on timestamps will result in immediate disqualification.

---

## 📉 Scoring Metric

Submissions are evaluated on the **Root Mean Squared Error (RMSE)** between the predicted wind speed and the actual observed wind speed.

$$RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$$

Where:
* $$n$$ is the number of images in the test set.
* $$y_i$$ is the actual wind speed (in knots).
* $$\hat{y}_i$$ is your predicted wind speed.

**Goal:** A lower RMSE is better. An RMSE of 0 means perfect prediction.

---

## 📝 Submission Format

For every image in the dataset, submission files should contain two columns: `Filename` and `WindSpeed`.

The file should contain a header and have the following format:

```
Filename,WindSpeed
2024al14_4kmirimg_202410051411.jpg,50.5
2024al14_4kmirimg_202410051416.jpg,112.0
2024al14_4kmirimg_202410051421.jpg,145.2
...
```