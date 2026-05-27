# IOAI Philippines 2026 - Round 2 Semi-Finals

Welcome to the **Quezon City Rainfall Sprint**! Congratulations on reaching the Semi-Finals. You are now competing for one of the **Top 20 spots** in the National Finals.
### **The Challenge**
Rainfall in a tropical urban environment like Quezon City is highly non-linear. It is influenced by seasonal monsoons — **Amihan** (Northeast Monsoon) and **Habagat** (Southwest Monsoon) — as well as localized heat-induced thunderstorms. 

You are provided with hourly weather features from 2020 to 2023, including:
* **Temperature & Humidity:** Key drivers of convective rain.
* **Wind Speed:** An indicator of seasonal shifts.
* **Atmospheric Pressure:** Critical for identifying incoming weather fronts.

**Your Goal:** Predict the exact amount of precipitation (in mm) for each hour of the 2023 test period.

---

### **Competition Structure**
* **Start:** Saturday, Feb 14, 2026, 00:00 PHT
* **End:** Sunday, Feb 15, 2026, 23:59 PHT
* **Evaluation:** Mean Absolute Error (MAE)
* **Leaderboard Split:**
    * **Public Leaderboard (30.7%):** Visible during the competition.
    * **Private Leaderboard (69.3%):** Determines final rankings and reveals after the deadline.

---

### **Critical Technical Requirements**
1. **Integer ID:** For grading compatibility, every submission must include the integer `id` column (0-8759). **Do not modify these IDs.**
2. **Reproducibility:** The Top 20 finalists will undergo a mandatory code review. We strongly recommend using the provided [Baseline Starter Notebook](https://drive.google.com/file/d/1NY8Qsb7KmhfTUElx69S7lW9HBkB4OStb/view?usp=drive_link) to ensure your environment and format are correct.
3. **Submission Limit:** 5 submissions per day.

---

### **How to Participate**
1. **Explore the Data:** Head to the **Data** tab to download your training and test sets.
2. **Handle the "id":** For grading compatibility, every submission must include the integer `id` column (0-8759). **Do not modify these IDs or their order**.
3. **Submit:** You are allowed **5 submissions per day**. Make them count!
4. **Environment:** You are required to use Kaggle Notebooks for reproducible research.

---

### **The "Final 20" Verification**
The Top 20 participants on the Private Leaderboard will undergo a mandatory **Code Review**. Ensure your notebooks are well-documented and reproducible. Plagiarism or the use of external 2023 weather data will result in immediate disqualification.

---

### **Real-World AI: The Quezon City Precipitation Challenge**

Predicting rainfall is one of the most complex tasks in meteorology, involving high-dimensional interactions between temperature, humidity, and atmospheric pressure. For the **IOAI Philippines 2026 Semi-Finals**, we have curated a multi-year hourly weather dataset specifically from **Quezon City**.

#### **The Problem Space**
As an AI researcher, your goal is to develop a model that can accurately forecast precipitation based on local sensor data. However, real-world data is "dirty." The sensors in this dataset have experienced calibration drift, missing intervals, and extreme outliers (such as 999% humidity readings). 

#### **Your Task**
You are provided with historical data from **2020 to 2022** to train your models. You must then generate predictions for every hour of **2023**. Success in this round requires more than just "fitting a model"—it requires:
* **Robust Data Cleaning:** Identifying and handling sensor errors.
* **Feature Engineering:** Creating time-based features (diurnal cycles, seasonality) to help your model understand Quezon City's weather patterns.
* **Generalization:** Building a model that performs well not just on the training data, but on the unseen 2023 test set.

#### **The Stakes**
This is a high-stakes "48-hour sprint." The **Top 20 participants** on the Private Leaderboard will advance to the National Finals. Consistency and reproducibility are key; your final rankings will be determined by the 70% of data you cannot see during the competition.

---

### **Evaluation Metric**

The performance of your model will be measured using **Mean Absolute Error (MAE)**. This metric calculates the average magnitude of the errors in your predictions, providing a direct sense of how many millimeters (mm) off your rainfall forecasts are on average.

The formula is defined as:
$$MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|$$

Where:
* $$n$$ is the total number of hours in the test set (8,760).
* $$y_i$$ is the actual precipitation (mm) for hour $$i$$.
* $$\hat{y}_i$$ is your predicted precipitation (mm) for hour $$i$$.

---

### **Submission Format**

For every `id` in the test set, you must predict a value for the `precipitation` column. Your submission must be a CSV file with a header and exactly 8,760 rows.

**CRITICAL:** The `id` column must be an **integer** (0-8759). Submissions using datetime strings or incorrect ID ranges will be rejected by the grading engine.

```
id,precipitation
0,0.0
1,0.5
2,1.2
...
8759,0.0
```
