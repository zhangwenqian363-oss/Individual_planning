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
