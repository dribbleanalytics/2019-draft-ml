# METHODOLOGY: Generating stats-based historical comparisons for the draft lottery

[Link to blog post.](https://dribbleanalytics.blog/2019/07/2019-draft-similarity)

## Data collection

First, I created a database of the stats of every lottery pick who played in college and was drafted in or after than the 1990 draft. The oldest draft used is 1990 because the NCAA added the three-point line in the 1986-87 season, so players drafted in 1990 played their entire career with a three-point line.

All data was taken from [Sports Reference](http://sports-reference.com/cbb).


## Similarity

I used cosine similarity and Euclidean distance to draw comparisons between this lottery and historical picks. The following stats were used to make the comparisons:

|Counting stats|Defensive stats|Advanced stats|
:--|:--|:--|
|G|STL|TS%|
|PTS|BLK|3PAr|
|AST|PF|FTr|
|TRB||WS|
|TOV|||


All data was standardized between 0 and 1 for the purpose of the similarity metrics. Each player in this year's lottery was compared to the entire historical database. 

I examined the five highest cosine similarity values and bottom five Euclidean distance values to make the comparisons.