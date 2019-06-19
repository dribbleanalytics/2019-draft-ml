# METHODOLOGY: Predicting the best scorers in the 2019 draft with machine learning

[Link to blog post.](https://dribbleanalytics.blog/2019/06/2019-draft-scorers-ml.html)

## Data collection

First, I created a database of all the shooting stats of projected first-round picks who played in college and were drafted in or later than the 1990 draft. The oldest draft used is 1990 because the NCAA added the 3-point line in the 1986-87 season, so players drafted in 1990 played their entire career with a 3-point line.

College data was taken from [Sports Reference](http://sports-reference.com/cbb). NBA data was taken from [Basketball Reference](http://basketball-reference.com).

The projected first-round picks were taken from [the Ringer's NBA mock draft](http://nbadraft.theringer.com) as of 6/15 update.

## Model creation

Out of the shooting stats collected, I used the following:

|Counting stats|Efficiency|Other|
:--|:--|:--|
|PPG|eFG%|Pick|
||FT%|SOS (strength of schedule)|
||3PAr||
||FTr||

Using scikit-learn, I created four models: a support vector regression, random forest regression, k-nearest neighbors regression, and extreme gradient boosting regression. Each model used scikit-learn's train test split function with a test size of 0.25.

The models' output was rookie year PPG. This is an improvement over last year's draft analyses, where career stats were used, thereby skewing the data towards players who had played more years.

## Predicting the best defenders in the draft

After creating the models, the 2019 draft's data was input to predict their rookie year PPG. The table below shows the results.

|Ringer mock draft rank (NCAA)|Player|SVM|RF|KNN|XGB|Average|
--:|:--|--:|--:|--:|--:|--:|
|1|Zion Williamson|15.2|16.2|15.3|15.8|15.6|
|2|Ja Morant|10.9|14.9|10.9|13.2|12.5|
|3|R.J. Barrett|14.2|12.7|14.1|12.5|13.4|
|4|Jarrett Culver|10.5|12.2|11.0|11.4|11.3|
|5|Deandre Hunter|9.2|7.5|9.0|9.3|8.7|
|6|Darius Garland|9.7|12.7|9.2|12.9|11.1|
|7|Coby White|9.8|12.4|10.1|10.1|10.6|
|8|Cam Reddish|8.7|9.8|8.7|7.9|8.8|
|9|Jaxson Hayes|7.1|6.9|7.0|6.9|7.0|
|10|Brandon Clarke|6.7|5.9|6.9|5.0|6.1|
|11|Rui Hachimura|5.8|6.4|5.5|5.6|5.8|
|12|Nassir Little|6.0|5.3|6.2|5.3|5.7|
|13|Nickeil Alexander-Walker|6.0|4.9|5.5|6.5|5.7|
|14|Romeo Langford|7.0|6.5|5.7|5.9|6.3|
|15|Keldon Johnson|5.9|6.5|5.7|5.7|5.9|
|16|Nicolas Claxton|4.0|3.7|5.3|4.2|4.3|
|17|Tyler Herro|5.5|5.6|5.0|5.9|5.5|
|18|P.J. Washington|4.9|6.7|6.0|5.0|5.6|
|19|Bol Bol|6.2|7.2|6.0|6.4|6.4|
|20|Ty Jerome|3.7|5.2|4.5|3.2|4.1|
|21|Matisse Thybulle|3.0|4.3|4.3|4.4|4.0|
|22|Cameron Johnson|3.7|5.5|4.6|4.3|4.5|
|23|Grant Williams|4.5|4.7|5.2|4.8|4.8|
|24|Kevin Porter|2.5|4.8|3.4|4.3|3.7|
|25|Talen Horton-Tucker|3.3|4.3|4.4|4.3|4.1|
|26|Carsen Edwards|4.5|5.3|4.9|4.9|4.9|
|27|Dylan Windler|2.4|5.2|4.8|5.2|4.4|
|28|Mfiondu Kabengele|2.8|5.0|4.1|4.5|4.1|
