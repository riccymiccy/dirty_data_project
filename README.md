# dirty_data_project


## Author
Ric Clark

I had two days to plan, clean and present data that needed to be cleaned and present some of my findings.

## Project Brief

The client wanted me to pick out a few insights about the data due to my great passion for track and field athletics.

## Tools

The data was from a dataset called decathlon that showed results from different competitions. I was coding in R.

The dashboard was created shinydashboard with the following libraries: 
- `library(tidyverse)`              
- `library(here)`
- `library(janitor)`


## How I spent my time
Day 1: I spent a long time trying to clean the data so that it was easily manipulated. In particular I was keen to pull out some intriguing insights and I did a lot of planning to determine what that might mean

Day 2: Having cleaned the data, I now used the diplyr verbs to answer those questions and produced a markdown document to give a presentation.



## Insights

Who had the longest long jump seen in the data?

`decathlon_analysis %>% 
  filter(events == "long_jump") %>% 
  arrange(desc(performance))`

![](/pictures/longest_long_jump.png)

What was the average 100m time in each competition?

`decathlon_analysis %>% 
  filter(events == "x100m") %>% 
  group_by(competition) %>% 
  summarise(average_100m = round(mean(performance),2))`

![](/pictures/average_100m.png)

Who had the highest total points across both competitions?

`decathlon_analysis %>%
  distinct(athlete, competition, points) %>% 
  group_by(athlete) %>% 
  summarise(total_points = sum(points)) %>% 
  arrange(desc(total_points))`
  
 ![](/pictures/highest_two_events_total.png) 
  
  What was the shot-put scores for the top three competitors in each competition?
  
  `decathlon_analysis %>%
  distinct(athlete, competition, events, performance) %>% 
  filter(events == "shot_put") %>% 
  filter(competition == "OlympicG") %>% 
  arrange(desc(performance))
  ecathlon_analysis %>%
  distinct(athlete, competition, events, performance) %>% 
  filter(events == "shot_put") %>% 
  filter(competition == "Decastar") %>% 
  arrange(desc(performance))`
  
 ![](/pictures/two_events_top_3_shot.png) 
  
  

### Key Take-aways

- As this a first attempt at cleaning data and presenting it, I realise now there are lots of ways to ask the questions.

- Practice is incredibly important to get data wrangling right and equally, once you have cleaned it once, you often go back and clean a second and third time before you can get it to do what you want.

- It's important to spend a lot of time trying to answer the business question before attempting to do anything. Writing down the plan is also equally important.