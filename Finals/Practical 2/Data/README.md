### 📊 Dataset Overview

This dataset consists of high-resolution infrared (IR) satellite imagery of two major hurricanes from the 2024 Atlantic Season: **Hurricane Beryl** and **Hurricane Milton**.

The goal is to predict the **Maximum Sustained Wind Speed (in Knots)** based solely on the visual structure of the storm.

---

### 📁 File Descriptions

* **`train.csv`** - The training set. Contains the filenames and ground truth wind speeds for **Hurricane Beryl**.
* **`test.csv`** - The test set. Contains the filenames for **Hurricane Milton**. You must predict the wind speed for these images.
* **`sample_submission.csv`** - A sample submission file in the correct format.
* **`Atlantic_Finals_Dataset.zip`** - A compressed folder containing two subfolders:
    * `/Beryl`: 500 images (Training)
    * `/Milton`: 500 images (Testing)

---

### 📝 Column Definitions

* **`Filename`**: The name of the image file (e.g., `2024al14_4kmirimg_202410070811.jpg`).
    * *Note:* The filename contains a timestamp, but your model should focus on visual features, not the date.
* **`WindSpeed`**: The target variable.
    * **Unit:** Knots (kt).
    * **Definition:** The maximum sustained wind speed (1-minute average) as defined by the National Hurricane Center.

---

### 🌪️ Storm Context (The Physics)

To build a good model, you should understand what you are looking at:

#### **1. Training Data: Hurricane Beryl (June-July 2024)**
* **Intensification:** Beryl was a "classic" rapid intensifier. It went from a disorganized Tropical Storm (35 kt) to a symmetrical Category 5 (145 kt) in roughly 48 hours.
* **Key Features to Learn:**
    * **Eye Formation:** Watch how the center clears out as wind speed increases.
    * **CDO (Central Dense Overcast):** A smooth, solid ring of clouds around the eye usually indicates a strong storm.

#### **2. Test Data: Hurricane Milton (October 2024)**
* **Intensification:** Milton was an "explosive" intensifier in the Gulf of Mexico.
* **Key Challenge:** Milton reached **155-160 knots** (stronger than Beryl). Your model must be able to extrapolate and recognize that a "perfect buzzsaw" shape means extreme danger (>150 kt).
* **Decay:** Milton also underwent an "Eyewall Replacement Cycle," where the eye became larger and fuzzier but the storm remained a Category 5. Can your AI tell the difference between a weakening storm and a restructuring one?

---

### ⚠️ A Note on Data Sources
These images are derived from the **GOES-16 Advanced Baseline Imager (ABI)**, specifically **Band 13 (Clean IR Longwave Window)**. This band is critical for estimating hurricane intensity because it highlights the temperature of the cloud tops (colder clouds = higher altitude = stronger convection).