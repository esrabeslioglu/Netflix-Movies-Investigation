# Netflix-Movies-Investigation

Netflix films are believed to have decreased in average duration over time. Let's make an interpretation based on the information in the dataset to determine whether there has indeed been a decrease in film durations.

Our dataset, named netflix_data.csv, contains the following information:

Column	        Description\
show_id	        The ID of the show\
type	          Type of show\
title	          Title of the show\
director	      Director of the show\
cast	          Cast of the show\
country    	    Country of origin\
date_added	    Date added to Netflix\
release_year	  Year of Netflix release\
duration	      Duration of the show in minutes\
description	    Description of the show\
genre	          Show genre

# Importing pandas and matplotlib
import pandas as pd\
import matplotlib.pyplot as plt

# Start coding!
netflix_df = pd.read_csv("netflix_data.csv")\
netflix_subset = netflix_df[netflix_df["type"] == "Movie"]\
netflix_movies = netflix_subset.loc[:, ["title", "country", "genre", "release_year", "duration"]]\
short_movies = netflix_movies[netflix_movies["duration"] < 60]\

colors = []\
for lab, row in netflix_movies.iterrows():\
    if row["genre"] == "Children":\
        colors.append("Pink")\
    elif row["genre"] == "Documentaries":\
        colors.append("Green")\
    elif  row["genre"] == "Stand-Up":\
        colors.append("Red")\
    else:\
        colors.append("Blue")\

# Now we need the graph of all these information
colors[:10]\
fig = plt.figure(figsize=(12,8))\
plt.scatter(netflix_movies.release_year, netflix_movies.duration, c = colors)\
plt.xlabel("Release year")\
plt.ylabel("Duration (min)")\
plt.title("Movie Duration by Year of Release")\
plt.show()

# It can not be said that there is a decrease in the durations of the movies
![image](https://github.com/esrabeslioglu/Netflix-Movies-Investigation/assets/52747952/ce2d4675-5f32-4103-8aa5-be3a21ab013b)

# So the result is maybe!
answer = "maybe"
