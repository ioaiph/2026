The dataset simulates a chaotic disaster response environment. It contains 10,000 unique records. A portion of the dataset is "noise" (e.g., spam texts, casual conversations) which must be accurately classified as non-emergencies. Additionally, 50 records represent critical audio radio intercepts.

### Files
* **`test.csv`**: The primary dataset containing the IDs, the raw SMS text, and the filenames of the audio intercepts. 
* **`audio_intercepts/`**: A folder containing 50 `.mp3` files. These are simulated shortwave radio transmissions utilizing dispatcher 10-codes (e.g., "10-50") and heavy background static.
* **`benchmark_submission.csv`**: A valid sample submission demonstrating the "melted" `RowId` and `Prediction` format required for scoring. 

### Columns in `test.csv`
* `id`: The unique integer ID for the record.
* `raw_text`: The raw SMS message. Contains heavy Taglish, abbreviations, and typos. *(Note: This is blank for audio records).*
* `audio_filename`: The name of the `.mp3` file in the `audio_intercepts` folder. *(Note: This is blank for SMS records).*

### Expected Output Classes
For each `id`, you must predict four targets to form your final `RowId` mapping:
1. `urgency_level`: Must be exactly one of `[Critical, High, Moderate, Non-Emergency]`.
2. `location`: The extracted location string (e.g., `marikina`, `valenzuela`). If no location is mentioned, output `Unknown`.
3. `needs_rescue`: Must be `Yes` or `No`.
4. `needs_medical`: Must be `Yes` or `No`.