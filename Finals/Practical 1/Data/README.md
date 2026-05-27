# IOAI Philippines 2026 Finals - Computer Vision Task

### Context
This dataset contains infrared satellite imagery of typhoons from the Western Pacific. The goal of this task is to estimate the intensity of a typhoon based on its visual appearance.

### Content
The dataset is split into training and testing sets:
* **train_images.zip**: 5,000 labeled images (2010-2019).
* **test_images.zip**: 1,000 unlabeled images (2020) for the competition leaderboard.
* **train.csv**: Contains the filenames and their corresponding `label` (Central Pressure in hPa).
* **test.csv**: Contains the filenames for the test set.

### Task
Build a regression model to predict the `label` (Pressure) for each image in the test set. Lower pressure indicates a stronger typhoon.

### Acknowledgements
Data derived from the Digital Typhoon Dataset (Kitamoto Lab, National Institute of Informatics).