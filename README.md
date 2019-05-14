# forestfire
Predict forest fire burn area

INTRODUCTION

Forest fire also known as wild fire which can spread quickly in a short time is one of the most destructive natural disaster. Fast detection of the fire is critical to forest firefighting. The use of automatic fore sensing devices has collected a large amount of meteorological data for data mining and prediction. This project will use the 3 years forest fire data from Montesinho natural park in Portugal to study what factors contributes to a forest fire and develop a model to predict the burn area. 

ABOUT THE DATA

1.	Source: http://www.dsi.uminho.pt/ ̃pcortez/forestfires/
2.	Time period: Jan 2000 to Dec 2003
3.	Total observations: 517
4.	Variables: 13

Variable	Description

X	x-axis spatial coordinate within the Montesinho park map: 1 to 9
Y	y-axis spatial coordinate within the Montesinho park map: 2 to 9
month	month of the year: ‘jan’ to ‘dec’
day	day of the week: ‘mon’ to ‘sun’
FFMC	FFMC index from the FWI system: 18.7 to 96.20
DMC	DMC index from the FWI system: 1.1 to 291.3
DC	DC index from the FWI system: 7.9 to 860.6
ISI	ISI index from the FWI system: 0.0 to 56.10
temp	temperature in Celsius degrees: 2.2 to 33.30
RH	relative humidity in %: 15.0 to 100
wind	wind speed in km/h: 0.40 to 9.40
rain	outside rain in mm/m2: 0.0 to 6.4
area	the burned area of the forest (in ha): 0.00 to 1090.84

METHOD AND VARIABLE SELECTION

The objective is to use meteorological data from 2000 to 2003 to predict burn area. I pre-processed and feature engineered the dataset and got a total of 36 independent variables as inputs to improve the performance machine learning and better predict the outcome variable (burn area).  I adopted RSME (Root Mean Square Error) to test the performance of 3 machine learning models

Pre-processing

When observing the burned area, I noticed that most of them distributed close to zero. So, I applied a log base 10 transform to the burn area to reduce skewness and improve symmetry. I also did centering and removed 9 near zero variance features. 

Variable and model selection

I made hypotheses that fires are more likely occur on weekends and affect by seasons.  As we see from figure 3, burn areas tend to be larger during the weekends than the weekdays. Figure 4 indicates that forest fire burn area does have seasonality. I introduced 2 new variables: “is_weekend” and “season” into the dataset and converted these categorical variables into binary features. 

I split the processed datasets into training and testing parts and applied the following regression model. Lasso model is the final model which has the lowest RMSE (Root Mean Square Error) of 0.6113552
1.	Forward regression
2.	Ridge regression
3.	Lasso regression

CONCLUSION AND RECOMMENDATIONS

Overall, all three models indicate that burn areas of forest fire are highly corelated to the time (weekend, season and month). Fires are more likely to happen on summer (July, August, September) and weekends. This may because more people will go to the national park in summer and weekends.  We suggest that there should be more forest ranger during the peak season. The national park should consider increasing the budget for propaganda fire prevention knowledge. The next step of the project is to include human activities data into our analysis and develop more features to increase the model performance.  

