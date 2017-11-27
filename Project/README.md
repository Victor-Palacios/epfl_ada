# SongOffensity
# Abstract
We investigate the development of colloquial language by looking at music. Popular music is mostly free of censorship and can be used as a repository of common expressions and phrases.
We analyse the lyrics collected in the MusixMatch database and develop a scheme to classify the “offensiveness” of a song.
In a first step, we investigate whether offensiveness is increasing over time.
Then we correlate the offensiveness of a song with its popularity. The 1 Million Song Database contains information on how often individual users have played a song. There is also an additional dataset of Yahoo reviews which can be connected to the MSD.
The fine-grained metadata in the million song database allows us to research these questions with respect to different artists and genres.

Today people take great pains to fight against all kinds of discrimination. One word out of line can cause online witch hunts. Maybe our trends can reveal a big hypocrisy: Are people really concerned or is offensiveness actually becoming more popular ?

# Research questions
Here are some questions we intend to answer:

- how to define / identify an offensive word and a swear word ? Are all offensive words equally offensive or should they be weighted somehow ?
- is there a trend over time that can be identified concerning the usage of offensive and swear words?
- which swear words are most commonly used ?
- how to define the popularity of a song ? We can use the counts a song has been played and we can integrate the Yahoo ratings dataset.
- does the popularity of a song correlate with its offensiveness and/or the number of swear words it contains ?
- are there popular and unpopular swear words ?
- can we identify different subsets of swear words that are more accepted ? This would mean that they are present in highly rated songs.

To expand on our insights, we would like to connect this a selection of Twitter data:
- if we have time, we would like to link the previously identified trend (if any) to the language the people use on social networks and see if the songs influence people’s behaviour and language

# Datasets
We expect to use the following datasets (more could be added later):
1. 1 million songs : https://labrosa.ee.columbia.edu/millionsong/
2. musixmatch: https://labrosa.ee.columbia.edu/millionsong/musixmatch
3. taste profile: https://labrosa.ee.columbia.edu/millionsong/tasteprofile
4. Yahoo ratings: https://labrosa.ee.columbia.edu/millionsong/pages/tasks-demos#yahoodata

The first dataset is the primary one. It includes the songs and various related futures. Some of them could be of great interest for us, like the song hotness, the artist hotness or the energy.
The second dataset provides the lyrics for a great subset of the the first dataset. We can use it to extract the offensive and swear words for each song.
The third and fourth datasets will help us in determining the popularity of the songs. They’re again linked (or can easily be) to the first dataset.

# A list of internal milestones up until project milestone 2
First we’ll have to download all the datasets, which in itself represents a challenge due to their size.
Then we’ll find a way to load the data and work with it (the whole dataset can’t fit in memory at once).
Once we can load the data, we will link the various datasets together to have all the required information for each song.

The offensiveness and popularity of a song are the two key metrics for our research. For milestone 2 we want to develop a solid rating scheme for them.

For the offensiveness
 - Identify swear words in the lyrics
 - Rate them by offensiveness
 - Rate songs by offensiveness

For the popularity
 - Find out how many times a song has been played
 - Filter and clean this data
 - Build scales based on the number of times a song has been played and the number of users that have played a song (how attractive is the song to individual users and how widespread is it)
 - Rate the popularity of a song

We also want to use the Yahoo ratings for the song popularity. There is existing code which links the msd to the yahoo ratings. We will investigate the quality of this mapping and try to integrate it into our research. We will use it to check our existing popularity rating for consistency and then decide how to merge the two ratings.


# Milestone 2
We have analysed the datasets we have. We don't know yet if we will use the Yahoo one because we noticed that this dataset doesn't rate songs but artists so we don't think that we will need it. The project structure is simple to understand: we put everything in the milestone_2_full_nb.ipynb notebook so that you can have everything in one place. This big notebook is simply a concatenation of the smaller ones with some additional code and text comments (the introduction for example). They are numbered following the order they appear in the main notebook. In the first 6 notebooks we explore how to measure the offensiveness of songs and in the last 2 we measure popularity because those two are the most important things we will need for the rest of the project.

# Things to do for milestone 3
Our main goals didn't change. We have analysed our datasets and they seem to be very good for what we wanted to do for our project.
