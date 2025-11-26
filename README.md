# NetFlicks: Football Goal Detection Model

## Overview
**NetFlicks** is a deep learning project developed to automate the detection of goal events in football (soccer) matches. The model utilizes a hybrid CNN-RNN architecture to analyze video footage as time-series data, identifying high-impact moments with high recall.

This project was developed by **Ron Balannik** and **Oded Neeman** as part of the Deep Learning Workshop at Tel Aviv University.

## Key Features
* **Goal Detection:** Classifies video frames to determine if a goal occurred.
* **Automated Data Pipeline:** The notebook automatically handles the downloading and preprocessing of the necessary video clips.
* **Hybrid Architecture:** Combines spatial feature extraction (CNN) with temporal sequence analysis (RNN).

## Technical Architecture
The model treats video classification as a sequence processing task:

1.  **Spatial Feature Extraction (EfficientNet-B0):** We utilize a pre-trained EfficientNet model to extract feature vectors from individual frames (224x398 pixels). The upper layers were fine-tuned to recognize football-specific patterns, while lower layers remained frozen.

2.  **Temporal Classification (Bi-LSTM):** A Bidirectional LSTM (Long Short-Term Memory) network analyzes the sequence of extracted features. It considers both past and future frames to determine if the current sequence constitutes a goal event.

## Dataset
The model works with the **SoccerNet v2** dataset, specifically focusing on match clips labeled for "Goal" events.

## Performance
The model was evaluated on a test set of 210 clips.

| Metric (Clip-Level) | Score | Notes |
| :--- | :--- | :--- |
| **Recall** | **100%** | The model successfully identified every clip containing a goal in the test set. |
| **Accuracy** | **89%** | The overall correct classification rate for clips. |
| **Specificity** | **80%** | The model correctly rejects 80% of non-goal clips. |

## Usage
The repository consists of a Jupyter Notebook that handles the end-to-end flow.

1.  **Clone the repository.**
2.  **Run the Notebook:** Open the `.ipynb` file (locally or in Google Colab).
3.  **Automatic Setup:** The code automatically downloads the required video samples and processes them; no manual data setup is required.
4.  **Important:** If running in Google Colab, you must change the file path where the notebook saves models and outputs. Look for and modify this line in the code:
    ```python
    filePath = "drive/MyDrive/videos/"  # <-- CHANGE THIS PATH
    ```

## Authors
* **Ron Balannik** - [GitHub](https://github.com/ronb2002)
* **Oded Neeman**
