---
layout: post
title: Regression Project
---
This project analyzed a data set of different aspects of video games. 
I wanted to look at this data to see if there were any trends in what types of video games sold the most. I figured that name, rating (like E or R), user ratings (which very extremely variable in how many users rated each game), publisher, and platform were either not important enough or not filled out enough to include. For Critic Score and Critic Count, I filled missing values with 0, because that's what they deserved for not putting up more complete data for me to use. When I looked at the histogram of my target variable, Global_Sales, I saw that the values are extremely concentrated on the low end of the range, meaning most games sell a certain amount, but a few sell extremely high. Then I briefly joined the one-hot for genre and the rest of the dataframe to use .corr to see which columns of the data most correlate with the target variable. Once I saw how strongly North American Sales, European Sales, Other Sales, and Japan Sales correlated, I realized that, obviously, those three things will basically completely account for Global Sales just from an arithmetic standpoint. The rest of the variables don't have a strong correlation, especially not the one-hot columns, even though I had hoped to see some trend with genre and popularity/sales. That's slightly sad because it means that it would be difficult to make a good model based off things other than sales for different parts of the world. Naturally, there's an optimal degree of 1, 2 and using a pipeline and degree 2 to make the polynomial values and scaling it is pretty simple. With ridgeCV, there is an R^2 very close to 1. The alpha was 1. 

My code repository can be found [here](https://github.com/supersophieminikittybabycakes/Regression_Project)