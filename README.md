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

Existing data sources (secondary):
* Steam Reviews https://www.kaggle.com/datasets/andrewmvd/steam-reviews 
* Steam Store Games (Clean dataset) https://www.kaggle.com/datasets/nikdavis/steam-store-games?select=steam_requirements_data.csv 
* Steam Player Data https://www.kaggle.com/datasets/jackogozaly/steam-player-data 
* Steam Game Analysis https://www.kaggle.com/code/simonprevoteaux/steam-game-analysis/data 
Steam API calls (primary) https://developer.valvesoftware.com/wiki/Steam_Web_API :
* GetNewsForApp
* GetGlobalAchievementPercentagesForApp
* GetPlayerSummaries
* GetFriendList
* GetPlayerAchievements
* GetUserStatsForGame
* GetOwnedGames
* GetRecentlyPlayedGames



