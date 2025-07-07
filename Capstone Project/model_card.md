# Model Card

## Model Description

**Input:** The model takes as input time-series data from 55 passive infrared (PIR) sensors, along with temperature readings. The PIR sensor data is preprocessed using `StandardScaler` to normalize the feature values.

**Output:** The model outputs a prediction for the presence detection label, which has been encoded using `LabelEncoder`. The possible output labels correspond to:
- Room is empty
- Stationary presence
- Active motion

**Model Architecture:** Three different deep learning model architectures were evaluated:

- **1D Convolutional Neural Network (CNN):** This model uses a `Conv1D` layer to extract features from the sequential PIR data, followed by a `MaxPooling1D` layer, a `Flatten` layer, and dense layers for classification.
- **Recurrent Neural Network (RNN) with GRU:** This model utilizes a `GRU` layer to capture temporal dependencies in the PIR data, followed by dense layers for classification.
- **Hybrid CNN-LSTM:** This model combines a `Conv1D` layer for feature extraction with an `LSTM` layer to capture sequential patterns, followed by dense layers for classification.

## Performance

The models were trained on `df_office1` and evaluated on `df_office2`. The performance was measured using accuracy and a classification report.

Based on the initial evaluations without extensive hyperparameter tuning:

* **Random Forest Accuracy:** `1.0000`
* **Gradient Boosting Accuracy:** `0.9963`
* **Neural Network Accuracy:** `0.9996`
* **CNN Accuracy:** `0.9864`
* **RNN (GRU) Accuracy:** `0.9872`
* **Hybrid CNN-LSTM Accuracy:** `0.9800`

All models achieved very high accuracy on the test dataset. The Random Forest and the basic Neural Network models showed perfect or near-perfect accuracy in this initial evaluation, while the deep learning models (CNN, RNN, and Hybrid) also performed very well, with accuracies above 0.98.

## Limitations

Outline the limitations of your model.

## Trade-offs

Outline any trade-offs of your model, such as any circumstances where the model exhibits performance issues. 
