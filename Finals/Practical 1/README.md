# IOAI Philippines 2026 National Finals - Practical 1 - Typhoon Intensity Estimation


## Goal
The Philippines is one of the most cyclone-prone nations globally. Accurate estimation of typhoon intensity is vital for effective disaster response and risk mitigation. Your objective is to develop a computer vision model that estimates a typhoon's intensity (**Central Pressure**) based on satellite imagery.

## Context
This challenge utilizes infrared satellite imagery of the Western Pacific captured between 2010 and 2020. The data originates from the **Digital Typhoon Dataset**, a long-term scientific record maintained by the **Kitamoto Lab at the National Institute of Informatics (NII)**, Japan.

## The Challenge
Participants are provided with:
* **Training Set**: 5,000 labeled images with known central pressure readings (2010–2019).
* **Test Set**: 1,000 unlabeled images from the year 2020.

**Target Variable**: `label` (Central Pressure in hPa). 
*Note: Lower pressure values signify higher typhoon intensity (e.g., 900 hPa is a super typhoon, while 1000 hPa is a tropical storm).*

---

## Goal
The Philippines sits in the most cyclone-prone waters on Earth. Accurate estimation of typhoon intensity is critical for disaster response. Your task is to build a computer vision model that can estimate the intensity (Central Pressure) of a typhoon solely from its satellite image.

## Context
This challenge uses infrared satellite imagery from the Western Pacific Ocean, captured between 2010 and 2020. The data is derived from the world-class Digital Typhoon dataset created by the Kitamoto Lab at the National Institute of Informatics (NII), Japan.

## The Challenge
You are provided with a training set of 5,000 labeled images (with known pressure readings) and a test set of 1,000 unlabeled images. Your model must predict the pressure for the test set.

**Target Variable:** `label` (Central Pressure in hPa).
* **Lower Pressure = Stronger Typhoon.**
* Example: 900 hPa is a Super Typhoon; 1000 hPa is a tropical storm.

---

## Metric
Submissions are evaluated on the **Root Mean Squared Error (RMSE)** between the predicted pressure and the actual observed pressure.

$$RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$$

Where:
* $$y_i$$ is the actual pressure.
* $$\hat{y}_i$$ is your predicted pressure.
* $$n$$ is the number of images in the test set.

## Submission Format
For every image in the dataset, submission files should contain two columns: `id` and `label`. The `id` must correspond to the filename (e.g., `2020010106-202001-MTS2-1.png`).

The file should contain a header and have the following format:

```
id,label
2020010106-202001-MTS2-1.png,980.5
2020010112-202001-MTS2-1.png,975.2
...
```