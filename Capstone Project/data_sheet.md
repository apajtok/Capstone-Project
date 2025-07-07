# Datasheet for PIRvision_FoG_presence_detection Dataset

### Motivation

* **For what purpose was the dataset created?**
    The dataset was created for occupancy detection tasks. The introductory paper, "Promoting Occupancy Detection Accuracy Using On-Device Lifelong Learning," suggests its purpose is to develop and evaluate machine learning models for detecting human presence, with a potential focus on on-device and lifelong learning applications.

* **Who created the dataset (e.g., which team, research group) and on behalf of which entity (e.g., company, institution, organization)? Who funded the creation of the dataset?**
    The dataset was created by Muhammad Emad-ud-din and Ya Wang, authors of the associated paper published in the *IEEE Sensors Journal*. The specific institution or funding sources are not mentioned in the provided information.

### Composition

* **What do the instances that comprise the dataset represent (e.g., documents, photos, people, countries)?**
    Each instance represents 4 seconds of recorded human activity, captured by a Passive Infra-Red (PIR) sensing node. The dataset contains 15,302 such instances.

* **How many instances of each type are there?**
    The dataset is labeled with three distinct classes:
    * `0`: Vacancy
    * `1`: Stationary human presence
    * `3`: Other activity/motion

    The specific count for each class is not provided in the summary.

* **Is there any missing data?**
    No, the dataset does not contain any missing values.

* **Does the dataset contain data that might be considered confidential?**
    The dataset does not contain direct personal identifiers like names or images. However, occupancy data can be sensitive as it reveals patterns of human presence and activity in private spaces like offices and residences.

### Collection Process

* **How was the data acquired?**
    The data was collected using a "Synchronized Low-Energy Electronically-chopped Passive Infra-Red sensing node" placed in residential and office environments.

* **If the data is a sample of a larger subset, what was the sampling strategy?**
    The provided information does not describe the sampling strategy.

* **Over what time frame was the data collected?**
    The dataset was donated to the UCI repository on January 4, 2025. The specific start and end dates of the data collection period are not mentioned.

### Preprocessing/Cleaning/Labelling

* **Was any preprocessing/cleaning/labeling of the data done?**
    Yes. The primary processing was labeling the instances based on the observed activity (Vacancy, Stationary, Other). The PIR sensor data is described as "55 raw analog sensor readings," suggesting minimal preprocessing of the feature data itself.

* **Was the “raw” data saved in addition to the preprocessed/cleaned/labeled data?**
    The data appears to be the "raw" sensor readings, which have been digitized and paired with labels.

### Uses

* **What other tasks could the dataset be used for?**
    Besides occupancy classification, the dataset could be used for:
    * **Anomaly Detection:** Identifying unusual patterns of movement or activity.
    * **Time-Series Forecasting:** Predicting future occupancy states.
    * **Energy Management Simulation:** Modeling the potential energy savings from smart HVAC and lighting systems based on real activity data.

* **Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses?**
    Yes. Since the data is collected from specific office and residential environments, models trained on it may not generalize perfectly to other types of spaces (e.g., industrial, retail) without further training. The high-fidelity sensor data might also capture patterns that are unique to the individuals observed, which could inadvertently bias a model if not handled carefully.

* **Is there anything that a dataset consumer might need to know to avoid uses that could result in unfair treatment of individuals or groups or other risks or harms?**
    Consumers should avoid using this data for surveillance or for making judgments about individual productivity or behavior (e.g., tracking employee break times). Such uses would be an invasion of privacy. To mitigate this risk, the data should only be used for its intended purpose, such as building automation and energy efficiency, and in a manner that respects user privacy and consent.

* **Are there tasks for which the dataset should not be used?**
    The dataset should not be used to identify or re-identify specific individuals. PIR sensors measure heat signatures and motion, not biometric data, and any attempt to use the data for such a purpose would be a misuse.

### Distribution

* **How has the dataset already been distributed?**
    The dataset is distributed via the UCI Machine Learning Repository.

* **Is it subject to any copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?**
    The provided information does not specify a license or terms of use. Datasets on the UCI repository are typically available for academic and research purposes.

### Maintenance

* **Who maintains the dataset?**
    The UCI Machine Learning Repository maintains the public availability of the dataset. The original creators (Muhammad Emad-ud-din and Ya Wang) are the primary contacts for questions regarding the data's content and collection.
