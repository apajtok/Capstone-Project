# Presence Detection using PIR Sensors and Machine Learning


## NON-TECHNICAL EXPLANATION

This project aims to create a smart system that can tell if someone is in a room just by using a special sensor called a PIR (Passive Infrared) sensor. Think of it like a motion detector, but smarter. Based on the sensor data, our system can figure out if a room is empty, if someone is sitting still, or if they are moving around. This helps automate things like turning lights or heating on and off, saving energy and making buildings more efficient. We used data collected from two different time periods in an office to train and test our models.

## DATA
The data used in this project comes from two CSV files, /content/pirvision_office_dataset1.csv and /content/pirvision_office_dataset2.csv. These datasets contain readings from 55 PIR sensors, along with a temperature reading, a timestamp, and a 'Label' indicating the presence state (empty, stationary, or active motion). The first dataset (df_office1) was used for training the models, and the second dataset (df_office2) was used for testing to evaluate how well the models generalize to new data.

## MODEL 
Machine learning models for presence detection:

* **Random Forest Classifier:** An ensemble method that builds multiple decision trees and combines their predictions. It's known for its robustness and good performance on various tasks.

* **Gradient Boosting Classifier:** Another ensemble method that builds trees sequentially, where each new tree corrects the errors of the previous ones. It often achieves high accuracy.

* **Neural Network (MLPClassifier):** A basic feedforward neural network with one hidden layer. Neural networks are powerful for learning complex patterns in data.

* **Convolutional Neural Network (CNN):** A type of deep learning model particularly effective for processing data with a grid-like topology, such as images or, in our case, the spatial arrangement of PIR sensors.

* **Recurrent Neural Network (RNN) - GRU:** A type of deep learning model designed for sequential data. GRUs (Gated Recurrent Units) are a variation of LSTMs and are good at capturing temporal dependencies in the PIR sensor readings.

* **Hybrid CNN-LSTM:** A model that combines the strengths of both CNNs and LSTMs, using CNN layers to extract spatial features from the sensor data and LSTM layers to capture temporal dependencies.

These models explore a range of approaches, from traditional machine learning to deep learning, to determine which performs best for this presence detection task.

## HYPERPARAMETER OPTIMSATION
For the traditional models (Random Forest, Gradient Boosting, and the basic Neural Network), default hyperparameters were used initially for evaluation.

For the deep learning models (CNN, RNN, and Hybrid CNN-LSTM), I planned to use Bayesian Optimization to find the optimal hyperparameters. However, I encountered compatibility issues with the libraries (scikit-learn, scikit-optimize, and scikeras) needed for this process. Due to these environment configuration challenges, Bayesian Optimization could not be fully implemented in the current setup. The results presented are based on the models trained with the hyperparameters defined in the code cells.

## RESULTS
Based on the initial evaluations without extensive hyperparameter tuning:

* **Random Forest Accuracy:** `1.0000`
* **Gradient Boosting Accuracy:** `0.9963`
* **Neural Network Accuracy:** `0.9996`
* **CNN Accuracy:** `0.9864`
* **RNN (GRU) Accuracy:** `0.9872`
* **Hybrid CNN-LSTM Accuracy:** `0.9800`

All models achieved very high accuracy on the test dataset. The Random Forest and the basic Neural Network models showed perfect or near-perfect accuracy in this initial evaluation, while the deep learning models (CNN, RNN, and Hybrid) also performed very well, with accuracies above 0.98.

### Learnings

* Even traditional machine learning models like Random Forest and a simple Neural Network can be highly effective for this presence detection task using PIR sensor data.
* The deep learning models also perform strongly, suggesting their potential for capturing complex patterns in the sensor data.
* The perfect or near-perfect accuracy on the test set might indicate that the test dataset is very similar to the training dataset, or that the task is highly separable with the given features. Further evaluation on more diverse datasets or with different cross-validation strategies would be beneficial to confirm the robustness of these results.
