## Using AI-Camera for People Tracking

**Roland Unger**

### Executive summary
**Project overview and goals:** <br>The goal of this project is to analyze the people moving and forecasting the movement for further action in an alarm control system.<br>
**Findings:**<br> The current best model is an `ARIMA` forecast model with an well performed forecast of 5 seconds.<br>
**Results and conclusion:**<br> The evaluation of the best model returned a comparsion with fitting time and forecast plots of the given dataset.<br>

### Rationale
In a common CCTV surveillance system an operator is watching abnormal behavior and reacting manually.
If the system is big, lets say 200 cameras, it is hard or unpossible to recognize the attacker.
Therefore a AI-model should filter and select the interesting cameras to the operator monitor.
Furthermore the model could start automatic actions on an alarm control system like:<br>
- Switch the selected cameras to an alarm monitor (multiple camera view on one monitor). 
- Predict the people moving from the last movement and see if the person will go over a specific virtual line (trip wire) in the near future. If so, an action could be released similar to point 1. The prediction gives the operator more time to react on the attacker´s behavior.  
- The predicting function of the model should find the person after covering from an other person in the picture or some other    object in the scene.
- The model should find abnormal behavior of people movement: Change of moving speed (slow to run), abnormal moving

### Research Question
The question this project aims to answer is what is the best forecast model with the fastest fitting and longest forecast time.

### Data Sources
The data source come from an AI-camera output meta data stream. The meta data contain <br>
- Timestamp of the detection
- Location of the detected object (x and y coordinates)
- Size of the object (bounding box)
- Classification (person, car, bike etc.)

### Methodology
First data cleaning and peparations was done. Furthermore the important features was selected and a base line ARIMA and LSTM model was set up.<br>
Next, with a cross validation function the best hyperparameter was selected. The results was stored in a comparsion dictionary and plotted for better understanding.

### Results
The most important finding was:
- A good ARIMA model need a high degree of lags.<br>
- A high degree of lags need a lot of fitting time.<br>
- A high fitting time is in most of the cases not possible, because of a forecast longer than 5 seconds is not applicable from the quality side.
- Comparing the two models with the MSE (mean squared error) the LSTM model shows better results (see List 5.1 and Figure 5.1).<br>
- Comparing the fitting or leaning time of the two differnet models also the LSTM model performs much better (see List 5.1 and  Figure 5.3). The LSTM model can fit in arround 2 seconds while the ARIMA model need arround 56 seconds. So the `LSTM` fit arround `20 times` faster. 
- Comparing the forecast ability the LSTM model performs much better (see List 5.1 and Figure 5.4). `LSTM` performs `40 times` better than the ARIMA model.

### Next steps
To get a better understanding, it could be interested to change the input data:
- with different moving speeds during the movement
- with many change of the moving directions

It could be interested to evaluate a `Kalman-Predictor` model and comparing with the LSTM.

### Outline of project

- [Link to notebook 1](https://github.com/te8titan/Capstone_project/tree/main/Capstone_Project_Roland_Unger.ipynb)
- [Link to data 2](https://github.com/te8titan/Capstone_project/tree/main/data)


### Contact and Further Information

Roland Unger
Email: te8@titan-electronic.com