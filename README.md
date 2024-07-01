# Netflix-Shows-and-Movies-Data-Analysis

# Project Overview
This project involves analyzing a dataset of Netflix shows and movies. The goal is to perform data preparation, exploration, and visualization using both Python and R. The dataset contains various attributes like title, director, cast, country, date added, release year, rating, duration, and genres.

# Dataset
The dataset contains information about Netflix shows and movies with the following columns:

show_id: Unique identifier for each show/movie.

type: Type of the entry (Movie/TV Show).

title: Title of the show/movie.

director: Director(s) of the show/movie.

cast: Main cast of the show/movie.

country: Country where the show/movie was produced.

date_added: Date when the show/movie was added to Netflix.

release_year: Release year of the show/movie.

rating: Rating of the show/movie.

duration: Duration of the show/movie.

listed_in: Genres of the show/movie.

description: Description of the show/movie.


Requirements
# Python Libraries
pandas
numpy
matplotlib
seaborn
zipfile

# R Libraries
ggplot2
dplyr
Setup

# Python Environment
import pandas as pd
# Load the dataset
df = pd.read_csv('Netflix_shows_movies.csv')
# Handle missing values and clean the data
df.dropna(inplace=True)

# Standardize the date format
df['date_added'] = pd.to_datetime(df['date_added'], format='%B %d, %Y')
# Save the cleaned dataset
df.to_csv('Netflix_shows_movies_cleaned.csv', index=False)

# R Environment
# Read the cleaned dataset
df <- read.csv("Netflix_shows_movies_cleaned.csv")

# Convert the date_added column to Date type
df$date_added <- as.Date(df$date_added, format="%Y-%m-%d")
library(ggplot2)
library(dplyr)

# Count the number of occurrences for each rating
rating_count <- df %>% 
  group_by(rating) %>% 
  summarise(count = n()) %>% 
  arrange(desc(count))

# Create the plot
ggplot(data=rating_count, aes(x=reorder(rating, -count), y=count)) +
  geom_bar(stat="identity", fill="steelblue") +
  theme_minimal() +
  labs(title="Distribution of Ratings", x="Rating", y="Count") +
  theme(axis.text.x = element_text(angle=45, hjust=1))


# Data Exploration

Descriptive Statistics
To understand the basic statistics of the dataset, we will explore the following:

Summary Statistics: Mean, median, mode, standard deviation, etc.
Distribution of Ratings: Frequency of each rating category.
Release Year Analysis: Number of shows/movies released each year.
Duration Analysis: Distribution of the duration of movies and TV shows.
