# Steam-Project
Project 4 using machine learning.

Proposal Project 4

Steam data sets

Steam Reviews
https://www.kaggle.com/datasets/andrewmvd/steam-reviews
Steam Store Games (Clean dataset)
https://www.kaggle.com/datasets/nikdavis/steam-store-games?select=steam_requirements_data.csv
Steam Player Data
https://www.kaggle.com/datasets/jackogozaly/steam-player-data
Steam Game Analysis
https://www.kaggle.com/code/simonprevoteaux/steam-game-analysis/data
developer.valvesoftware
https://developer.valvesoftware.com/wiki/Steam_Web_API#Formats

Using the data sets above we developed a few ideas for our project proposal : 

Kaggle dataset cleandata set Idea: Linking system requirement data with sales, reviews? 

Perhaps too difficult to parse the system requirements as they are not easily machine readable

Compare player numbers over time with news data? - keyword analysis or frequency analysis or both?
draw back, possibly unable to attain the data due to blocks, many of the users are ‘private’ users

Binary classification - find something (e.g. other games) that can predict positive or negative reviews for a particular game with over 75% certainty - kaggle/webscrape

Looking at the player reviews from steam for key words that are machine readable to predict game popularity.

From reviewed data set, look at unique user id and other features 

Formulate possible machine learning ideas from the steam.csv 

We are going to look at the above possibilities and decide on one after looking at the data we have.

# Proposal

We began to consider what data would be relevant to a developer, e.g. Skyhook games, creator of simulator software such as ‘Lawn Mowing Simulator’ and ‘Train Simulator’.
We found datasets on Kaggle but also realised we could use Steam’s own API to gather recent or historic data.  
We wondered if we could find some features of the data that would enable us to recommend any strategies for player engagement.  
Skyhook responded and said they did not use “machine learning to assess game development”, which gave us an opportunity to come up with some ideas for investigations and models we could create.  
We decided to look at the data to see if we could use machine learning to find any features that could model and predict player engagement so we could feed that back to them.  
Valve originally launched Steam to deliver and update their own creations, such as the multiplayer ‘Counter Strike’; however it has grown into ‘the largest digital distribution platform for PC gaming, estimated around 75% of the market share in 2013’ (https://en.wikipedia.org/wiki/Steam_(service))

### Existing data sources (secondary):
* Steam Reviews https://www.kaggle.com/datasets/andrewmvd/steam-reviews 
* Steam Store Games (Clean dataset) https://www.kaggle.com/datasets/nikdavis/steam-store-games?select=steam_requirements_data.csv 
* Steam Player Data https://www.kaggle.com/datasets/jackogozaly/steam-player-data 
* Steam Game Analysis https://www.kaggle.com/code/simonprevoteaux/steam-game-analysis/data 

### Steam API calls (primary) https://developer.valvesoftware.com/wiki/Steam_Web_API :
* GetNewsForApp
* GetGlobalAchievementPercentagesForApp
* GetPlayerSummaries
* GetFriendList
* GetPlayerAchievements
* GetUserStatsForGame
* GetOwnedGames
* GetRecentlyPlayedGames

# Suggested directions

* Linking system requirements data with sales or review scores
* Compare player numbers over time with news data
* Building a social network model of users, to find patterns in reviews
* Find some features that could be trained to predict review scores and popularity - e.g. other similar games
* Predicting average playtime from other data



# Files in this GITHUB

## Network Analysis

The purpose of this exploration was to try to find if there were similar patterns of behaviour (e.g. games owned, reviews, playtime, achievements) between closely related users. 

![image](https://user-images.githubusercontent.com/98031776/187021094-e3110c81-7763-47cd-a2cf-42b1d0881b05.png)


Enough (but not all) user have their profiles set to ‘public’ to make this interesting. However, having got to this point, scraping data for these users felt a long way from being able to train a machine learning algorithm on anything meaningful that we could use to help direct a developer. Here, the nodes are coloured for privacy, and sized for distance from the source node.


![image](https://user-images.githubusercontent.com/98031776/187021107-7b29d5b0-3255-46a0-b8c0-1a50d34e1c53.png)



## News Analysis
![image](https://user-images.githubusercontent.com/98031776/187021315-1d6e913d-e2ee-498e-9a83-932e76f7c974.png)

Does the ebb and flow of interest in a game depend on its presence in the media? What about community announcements, content updates, and the like? This could be undertaken as a frequency analysis of news items, or perhaps some natural language processing on the content of news items.

![image](https://user-images.githubusercontent.com/98031776/187021329-96f7d147-7a58-4e60-86b4-cfcac9e43112.png)

So you can see that there are definitely similar features with these graphs, even if they are not month-for-month the same…
![image](https://user-images.githubusercontent.com/98031776/187021347-28ce48c4-9dfe-4a84-bc6f-10fb0cef46bb.png)

As an initial experiment, Hyperparameter tuning a neural network produced a 64% accuracy result when filtering the data down to just one game, which I felt was an encouraging start, and perhaps by including more data, the algorithm would learn more features and find a good score of >75%

### Data cleaning steps:
* Handled in relational database style;
* Identified and removed testing periods from the data;
* Cleaning out inadequate data sources;
* Dropping initial rows - these would feature unreasonably high percentage increase, since the game had only just launched;
* Fixing data types;
* Cleaned out news sources with too few contributions.

### Results
* Accuracy scores, on predicting whether increase was positive or negative:
* Logistic regression: 53%
* Random Forest: 52%
* Neural Network: 55%

The link between monthly users and the news frequency is just not strong. /n

I went on to experiment in other ways, with blurring the data (moving average or gaussian style)... and trying linear regression (disastrous…) but I did not find any higher scores.  
Perhaps more blurring could help to find a link between… but the initial blur i tried did not improve the accuracy score.

Perhaps a finer detail of data for the player numbers, rather than average, as news items could have a momentary, day-to-day effect rather than across a month.



## Median Playtime Analysis






# Files NOT in this GITHUB

## System requirements analysis

A lack of consistency in how system requirements are laid out made this impossible for us to build into a reliable database.

![image](https://user-images.githubusercontent.com/98031776/187021249-8a78ff07-233f-49ad-a08f-1e9723b36552.png)
Pictured: system requirements for Lawn Mowing Simulator, Counter Strike: Global Offensive, and Vampire: The Masquerade: Bloodlines

This turned out to be too difficult to parse, due to the lack of a systematic structure for this information.


## Machine Learning on User Reviews
We tried to see if user reviews could be scraped from the Steam website, and then for each reviewer, build up a picture of other games they liked and disliked (Steam has a binary review system: thumbs up or thumbs down). This would enable us to train a logistic regression algorithm that could predict whether or not a particular user would like a given game, based on their other likes and dislikes. This would then enable us to identify users likely to appreciate the game, or perhaps find other games that had a similar profile.


![image](https://user-images.githubusercontent.com/98031776/187021214-c7aacfe2-4788-4a48-9850-79dfc5520ac6.png)
However, the data had a self-selection problem, where many users only give one type of review. Furthermore, the vast number of games available through Steam means that many users will have zero games in common with each other.  
At a practical level the website was also very good at refusing calls from webscraping algorithms, reducing the size of the dataset we could work from.

