# NBA-Accolades-Analysis


### Overview


My project submission seeks to analyze the objectivity of the NBA's yerly award selections - specifically for Most Valuable Player (MVP) and Defensive Player of the year (DPOY). Since these awards are voted on by members of the media, there is almost certainly a subjective component to the selection process. I am interested to see how closely yearly MVP and DPOY selections align with top performers in various statistical categories. Ultimately I will use a consolidated NBA dataset to build a classification model that learns from past selections to make predictions for future selections.


### Business And Data Understanding


My stakeholder for this project is the National Basketball Association (NBA). Up to this point, there has been little to no transparency offered into the yearly accolade selection process. I feel the NBA has a major opportunity to more clearly-define the accolade selection criteria. In order to help facilitate this process, I will analyze which features have been most important to predicting MVP and DPOY selections historically via classification modeling. The NBA can use this information along with future model predictions to not only establish a selection criteria, but also to supplement media voting with statistical backing.

The dataset I will be using for this analysis contains seasonal player data sourced from basketball-reference.com. The consolidated dataset contains over 20,000 rows anad 140 columns. These columns consist of various statistics (totals, per game, per 36 minutes, per 100 possessions, etc.) and the target variables will be "Rank-MVP" and "Rank-DPOY" transformed into categories (Won, Received Votes, Received No Votes).


I started my data exploration by looking at the dataset's features. There were a few categorical features (Team, Position, Playoffs) with the remaining features being all continuous. Many of the continuous variables were very highly correlated to one another due to the nature of their calculations - some of them used one or a few of the same underlying variables, and some were essentially the same stat just for a different time period (i.e. Points per game vs. Points per 36 minutes). Despite this, I still wanted to include a breadth of information to give the model more data points to learn from. Ultimately this was not an issue as I used a classification model instead of a regression one.


I next sought to understand how the dataset's features related to the target variables. I looked into the most highly-correlated features to "Rank-MVP" and "Rank-DPOY" and later supplemented this correlation analysis with feature importances from my final model.

### Data Pre-Processing

I took the following data cleaning steps to prepare for modeling:
- Removed special characters from player names
- Replaced Team = "TOT" or Total rows with most recent team names for players traded mid-season
- Mapped team name abbreviations accordingly to enable table joining
- Joined seasonal player tables with seasonal team tables with season MVP and DPOY voting tables
- One-Hot-Encoded categorical variables
- Replaced continuous variable null values with 0s after further exploration
- Created new, categorical target variables based on "Rank-MVP" and "Rank-DPOY"

With my newly-cleaned dataset, I conductd Exploratory Data Analysis (EDA) to get a better sense for trends in the data. My EDA included plotting time series graphs, measures of central tendancy (box-and-whisker), and scatter plots.

[INSERT EDA GRAPH SAMPLES HERE]

### Modeling Approach

I started my modeling process by splitting the cleaned dataset into Train and Test sets. For my baseline model - I built a multli-class Decision Tree Classifier that produced a Train Accuracy score of 100% and a Test Accuracy Score of 65% which suggested overfitting. Within the Test set classification report, I also noticed that the model performed much better on the majority class than the minority classes due to class imbalance. 

I took the following steps to iterate on my baseline model:
- Conducted SMOTE resampling to address class imbalance
- Incorporated hyperparameter tuning to address overfitting
- Changed dataset from multi-class to binary
- Tested Random Forest Classifiers and compared performance to that of Decision Tree Classifiers


### Modeling Results

