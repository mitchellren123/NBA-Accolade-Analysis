# NBA-Accolades-Analysis


### Overview


My project submission seeks to analyze the objectivity of the NBA's yerly award selections - specifically for Most Valuable Player (MVP) and Defensive Player of the year (DPOY). Since these awards are voted on by members of the media, there is almost certainly a subjective component to the selection process. I am interested to see how closely yearly MVP and DPOY selections align with top performers in various statistical categories. Ultimately I will use a consolidated NBA dataset to build a classification model that learns from past selections to make predictions for future selections.


### Business And Data Understanding


My stakeholder for this project is the National Basketball Association (NBA). Up to this point, there has been little to no transparency offered into the yearly accolade selection process. I feel the NBA has a major opportunity to more clearly-define the accolade selection criteria. In order to help facilitate this process, I will analyze which features have been most important to predicting MVP and DPOY selections historically via classification modeling. The NBA can use this information along with future model predictions to not only establish a selection criteria, but also to supplement media voting with statistical backing.

The dataset I will be using for this analysis contains seasonal player data sourced from basketball-reference.com. The consolidated dataset contains over 20,000 rows anad 140 columns. These columns consist of various statistics (totals, per game, per 36 minutes, per 100 possessions, etc.) and the target variables will be "Rank-MVP" and "Rank-DPOY" transformed into categories (Won, Received Votes, Received No Votes).


I started my data exploration by looking at the dataset's features. There were a few categorical features (Team, Position, Playoffs) with the remaining features being all continuous. Many of the continuous variables were very highly correlated to one another due to the nature of their calculations - some of them used one or a few of the same underlying variables, and some were essentially the same stat just for a different time period (i.e. Points per game vs. Points per 36 minutes). Despite this, I still wanted to include a breadth of information to give the model more data points to learn from. Ultimately this was not an issue as I used a classification model instead of a regression one.


I next sought to understand how the dataset's features related to the target variables. I looked into the most highly-correlated features to "Rank-MVP" and "Rank-DPOY" and later supplemented this correlation analysis with feature importances from my final model.

### Data Pre-Processing


