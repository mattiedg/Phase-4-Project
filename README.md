# Instagram User Likes Data
## Phase-4-Project

![Instagram_logo_2016 svg](https://user-images.githubusercontent.com/100098968/168591469-3bc1ff1e-06ec-4a51-96ef-fba4c91cc0a6.png)

# Business Problem

## At the onset of this project I started by looking at a problem that is important to all social media companies, retaining customers on their platform. To begin I sourced a data set from Kaggle that contained information on 1,100 Instagram users and their post data over time. This included information including the dates of all of their posts, the number of comments received on their posts, tags used on their posts, and likes received on their posts. To best look at usage on the Instagram app it seemed that taking a closer look at the likes data would be a good way to analyze users that were engaging with the app. 



# Data Analysis 

## The data within the set was very scattered at first, given that it had come from different users over the course of many years. To best analyze the larger trends in the data I combined these users by merging the data by summing the posts on specific days. This allowed me to look at a compact graph of the data over time. After looking at the graphs of the data it seemed that looking to analyze the data in a time series would be the best way to get a sense of usage as well as giving us the ability to model the series going forward and predict usage in the future. As well the daily time series for the data was extremely cluttered, this led me to not being able to analyze the data correctly, to continue I changed the periodicity of the data to monthly. 

<img width="770" alt="Screen Shot 2022-05-16 at 8 43 29 AM" src="https://user-images.githubusercontent.com/100098968/168595055-dea4ed8e-7a06-4cea-b265-4bc4cc37459f.png">

# Stationarizing the Data 

## After deciding on the time series method for predicting usage I had to check to make sure the data was right to use for time series. I performed a Dickey-Fuller test on the data to check that the mean and standard deviation were uniform over the time series and they were not. To stationarize the data I performed log transformations and square-root transformations to be able to create the rolling mean of the time series. With the rolling mean the data was still not stationary so I used differencing with the roll mean. Using this method proved successful and I received a p-value lower than .05 on the Dickey-Fuller test, allowing me to reject the null-hypothesis and say that the data is stationary. 

<img width="567" alt="Screen Shot 2022-05-16 at 8 49 29 AM" src="https://user-images.githubusercontent.com/100098968/168596164-08e7d5ae-2136-46eb-832c-a26e8573f911.png">
<img width="650" alt="Screen Shot 2022-05-16 at 8 49 39 AM" src="https://user-images.githubusercontent.com/100098968/168596123-71d1037b-7a37-4b19-a3f4-1fc41de38d09.png">

# Modelling the Data

## With the newly stationarized data I was able to now turn on to modelling the data. The question now is what model we could use to best predict the time series. As we are looking at likes data it was clear that we would need to look into the past to see how many likes posts had received in the past. This made me look to the Auto-Regression model. However we also needed to look forward to predict the data so as well a Moving Average model made sense. To reconcile the two I decided to use the ARMA(Auto-Regression/Moving Average) Model for analysis. I first ran the Auto Correlation and Partial Auto Correlation tests on the data. This gave me a good sense on what parameters to use with the ARMA model. I received the result of 2 and 2 which means that both the Moving Average and the Auto Regressor would be looking two days into the future and two days into the past, respectively, to make predictions. I initially ran the ARMA model with these parameters. The results had faily high AIC values so I tried near combinations of the parameter values. After testing the best result I received was with the ARMA (2,1) model. This gave me a good AIC score as well as low coefficients. With this model I was confident that this was the best way at looking at the data and predicting the data.

<img width="582" alt="Screen Shot 2022-05-16 at 8 59 49 AM" src="https://user-images.githubusercontent.com/100098968/168598058-30f6bef9-64e9-417d-8ebc-e2963127c274.png">

# Conclusion

## One of the main issues that appeared while analyzing the time series data was that the data was very one dimensional, meaning that we only had access to the raw likes and post data. To best be able to predict usage it would be extremely useful to have more data on the people that have posted, whether that be demographic information, time spend on the app, or engagement with other posts. There are myriad factors that would give us a best model for usage on the app. As well having access to data on posts and likes for more users would be extremely beneficial. However, given these constraints I do believe that analyzing the likes data is a good and worthwhile was of predicting future usage on the app. 
