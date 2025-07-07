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

Based on the datasheet, the main limitations of the dataset are:

Limited Generalizability: The data was collected exclusively in residential and office environments. This means that a model trained on this dataset may not perform well in other types of spaces, such as industrial or retail settings, without additional data.

Potential for Bias: The high-fidelity sensor data might have captured movement patterns that are unique to the specific individuals observed during the collection period. A model could inadvertently learn these individual-specific patterns instead of general human activity, which could bias its performance when faced with new, unseen individuals.

## Trade-offs

Issue Encountered: Bayesian Optimization with Keras Models
During the attempt to perform Bayesian Optimization for hyperparameter tuning of the Keras CNN model using scikit-optimize (skopt) and scikeras, we encountered an AttributeError: 'super' object has no attribute '__sklearn_tags__'.

Explanation of the Error:

This error typically arises when there is an incompatibility between the versions of the libraries being used, specifically scikit-learn, scikit-optimize, and scikeras. The scikeras library provides a wrapper (KerasClassifier or KerasRegressor) that allows Keras models to be used within the scikit-learn ecosystem, including with scikit-learn's model selection and hyperparameter tuning tools like BayesSearchCV from scikit-optimize.

The __sklearn_tags__ attribute is part of scikit-learn's internal mechanism for identifying estimator types and capabilities. The error indicates that the version of scikeras or scikit-optimize being used is not fully compatible with the installed version of scikit-learn (1.6.1), leading to a mismatch in how these libraries expect estimators to behave or expose their attributes.

Impact:

This compatibility issue prevents the skopt.BayesSearchCV from properly interacting with the scikeras.wrappers.KerasClassifier, halting the Bayesian Optimization process.

Resolution:

Resolving this error requires identifying and installing compatible versions of scikit-learn, scikit-optimize, and scikeras. This typically involves:

Checking the documentation of scikeras and scikit-optimize for recommended or required dependency versions.
Searching online resources (e.g., GitHub issues, forums) for reported compatibility issues and their solutions for the specific library versions.
Using the %pip install command to install a set of library versions that are known to be compatible.
Since this is an environment configuration issue, it cannot be fixed by simply modifying the code within the notebook cells. Manual intervention to manage library versions is necessary to enable Bayesian Optimization with Keras models in this environment.
