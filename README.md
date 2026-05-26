# Animation: An Analysis of Its Past & Present Around the World

## Table of Contents
* [Motivation](#motivation)
* [Questions](#questions)
* [Acquiring and Normalizing the Data](#acquiring-and-normalizing-the-data)
* [Problems and Challenges](#problems-and-challenges)
* [Technologies Used](#technologies-used)
* [Data Sources](#data-sources)

## Motivation
I have been interested in the art of animation for a long time. There have been a number of trends in the past few decades that I would like to explore and see where they are going. For instance, big budget animated films and shows in the US almost never use traditional animation anymore. Instead, they use digital animation (either 3D or 2D). While I think there are a lot of great movies and shows that use these techniques, I would hate to see the art of hand-drawn animation die off. 

## Questions
1) How have animation methods changed over the years? Can traditionally animated films still make a profit, or are they too expensive and time-consuming compared to digitally animated movies to be worthwhile?
2) How is the animation industry different across countries?
    - For instance, a lot of Japanese productions are still traditionally animated, and they are wildly popular both in their home country and abroad.
    - The film [*Nobody*](https://animationobsessive.substack.com/p/the-film-that-should-be-nominated) was a huge hit in China, and it made a lot of money on a small budget.


## Acquiring and Normalizing the Data
- I obtained the data for my analysis from several online movie databases, as I further discuss in the Data Sources section. I did this by using several APIs to download the data in Python. I then used pandas to put this data into DataFrames to make the data easier to use.
- I 

## Problems and Challenges 
- Where the data gave you issues - was merging the data painstaking? Did you have to leave behind a dataset and webscrape a new one? Did you have to spend days cleaning the data?

## Technologies Used
1) Python - used to gather the data using APIs and to clean, organize, and explore the data
    - pandas - turn the data into DataFrames and then into csv files that can more easily be used in Tableau
    - matplotlib/seaborn - create initial data visualizations to get an idea of what the data looks like
2) Tableau - create dashboards and further explore the data using more interactive visualizations
3) Git - version control 

## Data Sources
1) [MDBList API](https://api.mdblist.com/) - created the lists of traditional and computer animated films using this database because it had more robust and easy to use search function. I initially created the lists outside of the API using the search function on their website. Then I used the API in Python to obtain the list and save them into DataFrames. However, I found that the data from this database was not sufficient, so I looked elsewhere to get the data I needed.
2) [TMDB API](https://developer.themoviedb.org/) - where I got all of the data about each movie. I used this database because to had budget and revenue data, which was a key part of my analysis. There was also a [Python library](https://github.com/celiao/tmdbsimple/tree/master) someone had made for the API that made it easy to use.
