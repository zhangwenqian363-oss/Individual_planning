# Individual_planning

library(tidyverse)

players <- read_csv("players.csv")
sessions <- read_csv("sessions.csv")
players
sessions

1. Broad question: When (which time windows) is the number of simultaneous players likely to be large, so we can provision licenses with high probability?
2. Specific question we can gain from the dataset: Can we predict the hourly peak concurrent players (count of simultaneous players in each hour) using time features (hour-of-day, day-of-week), calendar indicators (holiday / event flags), and user mix (fraction premium / platform mix / region) in players.csv?
