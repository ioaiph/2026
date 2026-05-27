### **Dataset Overview**
The dataset consists of hourly weather observations for **Quezon City** from **2020 to 2023**. 
* **Training Data (2020-2022):** Historical observations including the target variable (`precipitation`).
* **Test Data (2023):** Observations for the year 2023. This file contains the features but **not** the target variable.

---

### **File Descriptions**
* **`ioai_qc_train.csv`**: The training set. Includes weather features and the actual hourly precipitation.
* **`TEST_FINAL_INT.csv`**: The test set. Use this file to generate your predictions for the year 2023.
* **`SUBMISSION_FINAL_INT.csv`**: A sample submission file in the correct format.

---

### **Data Fields**
* **`id`**: A unique integer identifier for each hour (0 to 8,759). **Required for submission.**
* **`datetime`**: The timestamp of the observation (YYYY-MM-DD HH:MM:SS).
* **`temp`**: Hourly temperature in Celsius.
* **`humidity`**: Relative humidity (%). *Note: Includes sensor noise/outliers.*
* **`pressure`**: Atmospheric pressure (hPa).
* **`wind_speed`**: Wind speed in m/s.
* **`precipitation`**: **(Target Variable)** Hourly rainfall in millimeters (mm).