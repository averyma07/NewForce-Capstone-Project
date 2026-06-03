# Animation: An Analysis of Its Past & Present Around the World

### [Interactive Dashboard](https://public.tableau.com/views/capstone_17792198304270/Cover?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) 
Note: The dashboard might look different on your computer than it does in my presentation due to different monitors (or maybe something else). All the same information is there though.

## Table of Contents
* [Motivation](#motivation)
* [Questions](#questions)
* [Acquiring and Normalizing the Data](#acquiring-and-normalizing-the-data)
* [Problems and Challenges](#problems-and-challenges)
* [Technologies Used](#technologies-used)
* [Data Sources](#data-sources)

## Motivation
I have been interested in the art of animation for a long time. There have been a number of trends in the past few decades that I would like to explore and see where they are going. For instance, big-budget animated films and shows in the US almost never use traditional animation anymore. Instead, they use digital animation (either 3D or 2D). While I think there are a lot of great movies and shows that use these techniques, I would hate to see the art of hand-drawn animation die off.

## Questions
1) How have animation methods changed over the years? Can traditionally animated films still make a profit, or are they too expensive and time-consuming compared to digitally animated movies to be worthwhile?
2) How is the animation industry different across countries?
    - For instance, a lot of Japanese productions are still traditionally animated, and they are wildly popular both in their home country and abroad.
    - The film [*Nobody*](https://animationobsessive.substack.com/p/the-film-that-should-be-nominated) was a huge hit in China, and it made a lot of money on a small budget.
3) What differences are there between traditional and computer-animated films? Are computer-animated films more likely to be made for children? Are most adult animated films traditionally animated?

## Acquiring and Normalizing the Data
- I obtained the data for my analysis from several online movie databases, as I further discuss in the Data Sources section. I did this by using several APIs to download the data in Python. I then used pandas to put this data into DataFrames to make the data easier to use.
- I removed several irrelevant columns, such as ID numbers for IMDB, and added several, such as
    - Release year and weekday
    - Revenue to budget ratio (revenue/budget)
    - Profit (revenue-budget)
    - Vote average normalized to vote count ([using this formula](https://math.stackexchange.com/questions/41459/how-can-i-calculate-most-popular-more-accurately/41513#41513))
    - Budget, revenue, and profit adjusted for inflation to 2025
 - The data I got from the APIs had the origin countries, genres, and production companies as lists of dictionaries. I ended up creating separate DataFrames/CSV files for each of these categories, using the movie ID as a foreign key.
 - I also downloaded the data for the casts and crews for each movie and created files for these, too.

## Problems and Challenges 
- One of the first challenges I had was with the data columns that were lists of dictionaries (as discussed above in Acquiring and Normalizing the Data) and figuring out the best way to store them. Initially, I converted them to strings, with each item separated by commas (e.g., Animation, Family, Comedy). However, I ran into issues with the production companies, as some of them had commas in their names. I then tried putting quotes around the production company names, but I then found out that some of them also had quotes! Finally, I came up with the solution of creating separate DataFrames/CSV files for each of these columns and connect it to the main dataset with the movie ID as a foreign key.
   - Ex:
     | movie_id | genre |
     | --- | --- |
     | 1 | Animation |
     | 1 | Family |
     | 1 | Comedy |
- I also had a problem when I first started importing my data into Tableau. I had separated the data for traditional and computer animation, and I tried to keep them separate in Tableau. However, this created problems when I tried to put the data from both datasets on the same graph. I ended up unioning my data for traditional and computer animation in Tableau. This ended up being easier than what I was trying to do in the first place.

## Technologies Used
1) Python - used to gather the data using APIs and to clean, organize, and explore the data
    - pandas - turn the data into DataFrames and then into CSV files that can more easily be used in Tableau
    - matplotlib/seaborn - create initial data visualizations to get an idea of what the data looks like
2) Tableau - create dashboards and further explore the data using more interactive visualizations
3) Git - version control 

## Data Sources
1) [MDBList API](https://api.mdblist.com/) - created the lists of traditional and computer animated films using this database because it had a more robust and easy-to-use search function. I initially created the lists outside of the API using the search function on their website. Then, I used the API in Python to obtain the list and save them into DataFrames. However, I found that the data from this database was not sufficient, so I looked elsewhere to get the data I needed.
2) [TMDB API](https://developer.themoviedb.org/) - where I got all of the data about each movie. I used this database because it had budget and revenue data, which was a key part of my analysis. There was also a [Python library](https://github.com/celiao/tmdbsimple/tree/master) someone had made for the API that made it easy to use.
3) [CPI Data 1913-2026](https://github.com/datasets/cpi-us/blob/main/data/cpiai.csv) - used to adjust monetary columns for inflation
4) [Countries with Regional Codes](https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/blob/master/all/all.csv) - all of the countries in the main data were written as two-letter codes, so I needed this dataset 
