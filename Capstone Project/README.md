# PROJECT TITLE 


## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
The goal of the machine learning model is presence detection.
In other words, based on data from a passive infrared (PIR) sensor, the model determines if someone is currently present in a given room.
What does this mean in practice?
The model can distinguish between different states:
•	The room is empty: No one is in the sensor's field of view.
•	Stationary presence: Someone is in the room but is not moving much (e.g., reading or sitting at a desk).
•	Active motion: Someone is currently moving in the room.
The main goal of this technology is most often to increase automation and energy efficiency. For example, a smart home system can automatically turn off the lights and heating in an empty room, thereby saving energy.

## DATA
A summary of the data you’re using, remembering to include where you got it and any relevant citations. 
https://archive.ics.uci.edu/dataset/1101/pirvision_fog_presence_detection

## MODEL 
A summary of the model you’re using and why you chose it. 
•	Random Forest: An ensemble of decision trees that is robust and generally performs well on a wide range of problems. It's a good baseline model.
•	Gradient Boosting Machines (e.g., XGBoost, LightGBM): These are highly effective ensemble methods that build trees sequentially, with each new tree correcting the errors of the previous ones. They often achieve state-of-the-art performance on tabular data

## HYPERPARAMETER OPTIMSATION
Description of which hyperparameters you have and how you chose to optimise them. 

## RESULTS
A summary of your results and what you can learn from your model 

You can include images of plots using the code below:
![Screenshot](image.png)

## (OPTIONAL: CONTACT DETAILS)
If you are planning on making your github repo public you may wish to include some contact information such as a link to your twitter or an email address. 


