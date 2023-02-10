--- 

# NBA Combine Data Analysis

--- 

## Executive Summary


### Problem Statement
I will use regression models to build a rankings system on the the NBA combine draft and College basketball data. Utilizing the stats from the NBA combine via stats.nba.com, I will construct a model to predict the target variable of Win Share per player. From the College basketball data I will utilize the:

WS — Basketball Reference defines a Win Share as “a player statistic which attempts to divvy up credit for team success to the individuals on the team.”¶ (https://www.basketball-reference.com/about/ws.html)

I plan on creating 13 unique players with different attributes to see how they affect their Win Share based off my analysis. By looking into this problem, this could potentially help NBA teams and College Basketball Teams evaluate new players and determine what type of impact they can make on their team.

### Description of Data
Datasets that were created through data cleaning and preprocessing:

-nba_draft_data.csv: NBA Combine data from 2000 - 2022

-College_WS.csv: Dataframe with player's College Win/Share stat from their last season

-Final_dataset_Cleaned.csv: Final Dataframe that combines the two previous dataset & is cleaned of all null and missing values

#### Size
-nba_draft_data.csv: 1552 rows and 47 columns

-College_WS.csv: 1552 rows and 48 columns

-Final_dataset_Cleaned.csv: 1278 rows and 17 columns

-Test Data.xlsx: 17 rows and 14 columns

-Result_Data.csv: 13 rows and 14 colummns


#### Source
I collected data from two different locations:
1. https://www.nba.com/stats/draft/combine
2. https://www.sports-reference.com/cbb/

-The NBA combine data was collected using an API wrapper labeled as: py_ball (https://github.com/basketballrelativity/py_ball)

-The College Win Share data was collected using a for loop using: pandas.read_html
#### Target
Target is a regression analysis predicting the Win Share for a new group of players

Target Audience: Basketball teams, NBA and college, looking to improve their team. 

#### Data Dictionary
Data Dictionary of the differnt features used in my project.

|Feature|Type|Dataset|Description|
|---|---|---|---|
|Season|integer|Final_dataset_Cleaned|The year in which the player's data was collected in|
|Player_ID|integer|Final_dataset_Cleaned|Specific number per player as an identification label |
|First_Name|object|Final_dataset_Cleaned|First name of the player|
|Last_Name|object|Final_dataset_Cleaned|Last name of the player|
|Player_Name|object|Final_dataset_Cleaned|Full name of player|
|Position|object|Final_dataset_Cleaned|Position of which the player represents|
|Height_W_Shoes|float|Final_dataset_Cleaned|Height of player in shoes recorded in inches|
|Weight|float|Final_dataset_Cleaned|Weight of player recorded in pounds|
|Winspan|float|Final_dataset_Cleaned|Length of players wingspan recorded in inches|
|Standing_Reach|float|Final_dataset_Cleaned|The Length of a players reach with their arm pointed upwards recorded in inches|
|Body_Fat_Pct|float|Final_dataset_Cleaned|Body fat percentage of player|
|Hand_Length|float|Final_dataset_Cleaned|Length of players hand recorded in inches|
|Hand_Width|object|Final_dataset_Cleaned|Width of players hand recorded in inches|
|Standing_Vertical_Leap|datetime|Final_dataset_Cleaned|Measurment of how high a person jumps without a running start, recorded in inches|  
|Max_Vertical_Leap|float|Final_dataset_Cleaned|Measurment of how high a person jumps with a running start, recorded in inches|  
|Lane_Agility_Time|float|Final_dataset_Cleaned|Test to measure the agility of a  player, recorded in seconds|
|College WS|float|Final_dataset_Cleaned|Player's recorded College Win Share for their last collegiate season|


#### Model 1:  Performance on Training/Test Data
##### Features Included:

- Position, Height with shoes, Weight, Wingspan, Standing reach, Body fat percentage, Hand length, Hand width, Standing vertical leap, Max vertical leap, Lane agility time

|Model|Train RMSE|Test RMSE|
|---|---|---|
|Linear Regression|2.099|1.944|
|Ridge Regression|1.969|2.008|
|Lasso Regression|1.973|2.005|
|Decision Tree|1.921|2.096|
|Decision Tree: Gridsearch|1.870|2.032|
|Random Forest: Gridsearch|1.870|1.998|

#### Model 2:  Performance on Training/Test Data
##### Features Included:

- Position, Height with shoes, Wingspan, Standing reach, Hand length, Hand width, Standing vertical leap, Max vertical leap

|Model|Train RMSE|Test RMSE|
|---|---|---|
|Linear Regression|2.105|1.967|
|Ridge Regression|1.992|2.0155|
|Lasso Regression|1.997|2.021|

### Conclusion
This project showed the importance of each event at the NBA Combine and how it can affect a player's win share.  Out of all 
the models I ran (linear regression, ridge regression, lasso regression, decision tree, and random forest) linear regression
produced the lowest RMSE.  After creating fake players and running it through the optimal model I can predict the potential 
value of a player using Win Share as the metric.  These Results showed:

    a.) Features such as Wingspan, Weight are some of the most important columns that can affect the potential of a player
    b.) Features such as Height, Vertical, Lane Agility are somewhat useful predictors
    c.) The rest of the features: hand size, body fat pct, and standing reach are not helpful predictors.
    
This project allowed me to see the importance of each event in the NBA Combine.  Besides showing the importance of each 
even in the NBA Combine, it can also be used as a way to measure the value of a player for both college and NBA teams.
This tool can help basketball scouts "size" up players and give a legitmate metric value.  This can help teams see the 
potential in a player purely based off physical traits(vertical, speed, height, weight etc.)  Based off this model it also 
shows the value per position and altered NBA Combine stats could be helpful.  For example:

    a.) Player 11  shows that a Center who has is smaller, less vertical, and reach, but who is extra big and long
    wingspan, can produce a higher Win Share compared to other centers.
    
Overall, this model can give more insight and better data on basketball players given their NBA combine data.  The Predicted Win Share column shows that for players 0-9 do not differ greatly.  This shows that overall the features I used did not show a great difference.  However, with the highly altered player, it shows that certain players with extreme traits in certain physical traits(Weight, Agility, Wingspan) could produce a higher win share.

Basketball growing and becoming a bigger business in the NBA and college.  This insight can help give the edge for 
any basketball team trying to win more.
### Next Steps

Potential next steps would be to add more features such as:
a.) 3 pt. shooting
b.) Defensive stats (steals & blocks.

Basketball is an evolving sport and shooting, especially 3 pointers, are becoming more valuable for a team.  Also, looking at defensive
stats can give better insight and accuray to the model.