---
layout: post
title: Classification Project
---
The reputation of for-profit colleges in America has been somewhat sketchy as of late--in my mind, educating to make money while doing just enough to attract paying students is not the best model for academic success. I’ve been told that things like Trump University and other career-based schools are both expensive and known to generally have worse outcomes when compared to nonprofits.

After reading a huge dataset of colleges from the Department of education, the intention was to see if we could use machine learning to predict for-profit or non-profit status using an array of factors. Using the k-best function you can see that there are a few factors that correlate strongly (online_only, ind_low_income, and retention_listed_y_n).
 
I used a multitude of models from the package scikitlearn, so there were many different algorithms to model and predict the target variable (profit status). The model GradientDescent yielded the best AUC on the ROC curve which shows two metrics of correct identifications on the testing data. It was cool and also a little depressing to see how accurately machine learning models could predict for-profit status--that means that for-profit schools are generally distinct and identifiable in comparison to non-profits, probably in a negative way.


Ever since US News published their first list, numerical college rankings have become not only popular but highly influential on the decisions of students and the outcomes for colleges. For example, colleges who are ranked highly or surge up in rank number from one year to another are likely to see a jump in quantity and quality of applicants. However, there’s uncertainty about what factors should be considered in the ranking system.

I wanted to try ranking colleges by things that are more based on outcomes for students since the intention of college is to improve outcomes. As z-score scaled factors, I added: retention, 7-year repayment completion (multiplied by 3), instructional expenditure per student, and accreditation. The worst ten colleges (that had names shown) when I printed out the tail of the dataframe indexed by the sum score was:

Florida Barber Academy
National American University - Richardson
Stroudsburg School of Cosmetology
Armstrong State University
Carrington College - Reno
Brightwood Career Institute - Broomall
Slippery Rock University of Pennsylvania
Aerosim Flight Academy
International College of Broadcasting (the very worst one)

There’s a clear trend - most of these colleges are vocationally-focused, and most happen to also be for-profit schools (my use of accreditation as a factor probably had something to do with that). When I looked at the tail of the dataframe, it was visible that there was a combination of factors pushing all these schools to the bottom - all had poor 7-year repayment (because I prioritized that in my scoring system) but some had good retention while having mediocre instructional expenditure; it really varied.

If I were a governmental organization overseeing accreditation, I would particularly look at the ratio between tuition revenue and instructional expenditure per student. If a college is taking in a lot and spending little on its students, that is a sign of predatory behavior. False promises and statistics is also a sign of predatory behavior; this marketing is often directed towards disadvantaged groups to enroll people under false pretenses [here](https://blog.harvardlawreview.org/for-profit-schools-predatory-practices-and-students-of-color-a-mission-to-enroll-rather-than-educate). Gratuitous and more freely given loans might seem like a blessing for students who want a college education, but without forgiveness systems, those loans build up interest over time and are hard to pay off, leaving students with tons of debt, especially if the school didn’t prepare them well [here](https://bigthink.com/politics-current-affairs/predatory-student-loans). To evaluate a college’s legitimacy, I would look at not just the 7-year declining loan balance as a sign of adequate preparation, but also other career statistics like employment in their fields. 


My code repository can be found [here](https://github.com/supersophieminikittybabycakes/Classification_Project)