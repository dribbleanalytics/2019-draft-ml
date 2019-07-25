# METHODOLOGY: Using machine learning to predict All-Stars from the 2019 draft

[Link to blog post.](https://dribbleanalytics.blog/2019/07/2019-draft-ml-all-stars)

## Data collection

First, I created a database of top-10 picks who played in college and were drafted between 1990-2015 drafts (inclusive). The oldest draft used is 1990 because the NCAA added the three-point line in the 1986-87 season, so players drafted in 1990 played their entire career with a three-point line. The 2015 draft is used as the upper limit so that all players played their entire rookie contracts and had a chance to make an All-Star team.

College data was taken from [Sports Reference](http://sports-reference.com/cbb). All-Star data was taken from this [Basketball Reference page](https://www.basketball-reference.com/awards/all_star_by_player.html).

## Model creation

Out of the stats collected, I used the following as model inputs to predict whether a player will make an All-Star team:

|Counting stats|Efficiency|Other|
:--|:--|:--|
|PPG|TS%|Pick|
|TRB|3PAr|SOS|
|AST|FTr||
|STL|||
|BLK|||

Using scikit-learn, I created four models: a logistic classifier, a support vector classifier, a random forest classifier, and a gradient boosting classifier. Hyparameters were tuned using grid search, and each model was built with a scikti-learn train/test split with a test size of 0.25.

We examined the prediction probabilities to give each prospect an All-Star probability.

## Results

After creating the models, the 2019 draft's data was input to predict theri All-Star likelihood. The table below shows the results.

|Pick|Player|LOG|SVC|RF|GBC|Average|
--:|:--|--:|--:|--:|--:|--:|
|1|Zion Williamson|0.71|0.63|0.80|1.00|0.78|
|2|Ja Morant|0.65|0.49|0.58|0.91|0.66|
|3|RJ Barrett|0.37|0.49|0.53|0.62|0.50|
|4|DeAndre Hunter|0.22|0.23|0.16|0.00|0.15|
|5|Darius Garland|0.19|0.24|0.42|0.10|0.23|
|6|Jarrett Culver|0.25|0.30|0.48|0.47|0.37|
|7|Coby White|0.15|0.27|0.31|0.16|0.22|
|8|Jaxson Hayes|0.08|0.17|0.61|0.94|0.45|
|9|Rui Hachimura|0.07|0.11|0.17|0.00|0.09|
|10|Cam Reddish|0.10|0.20|0.35|0.28|0.23|

To find good value picks, we compared each player's All-Star probability to the percent of player drafted at his slot who made an All-Star. The table below shows the relative value.

|Pick|Player|All-Star % at pick # since 1990|Average prediction|Difference|
--:|:--|--:|--:|--:|
|1|Zion Williamson|0.64|0.78|0.14|
|2|Ja Morant|0.4|0.66|0.26|
|3|RJ Barrett|0.56|0.50|-0.06|
|4|DeAndre Hunter|0.32|0.15|-0.17|
|5|Darius Garland|0.4|0.23|-0.17|
|6|Jarrett Culver|0.24|0.37|0.13|
|7|Coby White|0.08|0.22|0.14|
|8|Jaxson Hayes|0.2|0.45|0.25|
|9|Rui Hachimura|0.16|0.09|-0.07|
|10|Cam Reddish|0.12|0.23|0.11|
