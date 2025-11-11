# Individual_planning

library(tidyverse)

players <- read_csv("players.csv")
sessions <- read_csv("sessions.csv")
players
sessions

1. Broad question: When (which time windows) is the number of simultaneous players likely to be large, so we can provision licenses with high probability?

2. Specific question we can gain from the dataset: Can we predict the hourly peak concurrent players (count of simultaneous players in each hour) using time features (hour-of-day, day-of-week), calendar indicators (holiday / event flags), and user mix (fraction premium / platform mix / region) in players.csv?


3. The dataset we've got:
- `players.csv` (196 rows × 7 columns). Key fields found: `experience`, `subscribe`, `hashedEmail`, `played_hours`, `name`, `gender`, `Age` (Age has 2 missing values).
- `sessions.csv` (1,535 rows × 5 columns; after cleaning 1,529 usable sessions). Key fields: `hashedEmail`, `start_time`, `end_time`, `original_start_time`, `original_end_time`. Two `end_time` values were missing and were temporarily filled with `start_time + 1 minute` for EDA.
- Observations: 196 unique players; 1,529 usable sessions after cleaning. Timestamp parsing required UTC assumption; convert to local timezone if needed.


4. Exploratory Data Analysis and Visualization
For player data set, compute the mean of each numeric variable in players.csv first. This helps identify overall trends in player attributes such as age and playtime. Then explore playtime differences by subscription status: subscription type may correlate with play intensity or session frequency.

The session data set records more information about play session, including start and end times. To explore the time window which has the most players, first, create a new variable in sessions.csv for session duration in minutes. Aggregate sessions by hour to visualize concurrency trends. This shows which hours of the day have the most active sessions.


5. Methods and Plans
For this project, I suggest to use a multiple linear regression model to explore the relationship between player engagement and performance metrics. Specifically, the model will be used to predict a continuous outcome variable (such as total playtime or average session length) based on explanatory variables such as number of sessions, session frequency, or in-game attributes from players.csv.

Multiple linear regression is suitable because:

The main variables of interest (e.g., playtime, sessions, achievements) are quantitative and continuous.

It allows for interpretation of coefficients, providing insight into how much each predictor affects the target variable.

It is a transparent, interpretable starting point for modeling — appropriate for an initial analysis before applying more complex models like random forests or gradient boosting.

This method aligns well with the goal of explanation and understanding, rather than prediction accuracy alone.

The limit of multiple linear regression model is that the real player behavior may be non-linear, meaning linear regression could oversimplify complex relationships. Also, some outliers (e.g., extremely active players) can affect results.
