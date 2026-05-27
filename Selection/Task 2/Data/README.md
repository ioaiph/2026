In this challenge, you are provided with a collection of aerial drone images captured over various Philippine coastal regions. The goal is to detect and localize standard maritime objects and identify hidden anomalies.

### Folder Structure
* **train_images/** - A set of images for training your object detection models.
* **test_images/** - The evaluation set. You must generate predictions for these images.
* **train_labels.csv - Ground truth annotations for the training set.
* **sample_submission.csv - A sample submission file in the correct format.

### CSV Column Definitions
* `image_id`: The filename of the image (e.g., `123.jpg`).
* `annotations`: Ground truth bounding boxes in the format `class_id x1 y1 x2 y2`.
* `PredictionString`: (Submission only) Your predicted boxes in the format `class_id confidence x1 y1 x2 y2`.
* `easter_egg_found`: A classification label identifying any rare anomalies found in the image.

### The Classes
| Class ID | Object Name | Notes |
| :--- | :--- | :--- |
| **0** | Swimmer | Individuals in the water. |
| **1** | Boat | Various watercraft (bancas, yachts, etc). |
| **2** | Debris | Floating objects/trash. |
| **8** | Soggy Bunny | **Anomaly:** Not present in training data. |
| **9** | Painted Egg | **Anomaly:** Not present in training data. |

### Note on Anomalies
The Training Set contains only Classes 0, 1, and 2. Classes 8 and 9 are "Out-of-Distribution" (OOD) and appear only in the Test Set. You are expected to use Generative AI (to create synthetic training data) or Vision-Language Models (to perform zero-shot detection) to find these hidden targets.