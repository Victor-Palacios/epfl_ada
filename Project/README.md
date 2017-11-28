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

## Project structure
The project structure is simple to understand: we put everything in the milestone_2_full_nb.ipynb notebook so that you can have everything in one place. This big notebook is simply a concatenation of the smaller ones with some additional code and text comments (the introduction for example). They are numbered following the order they appear in the main notebook. In the first 6 notebooks we explore how to measure the offensiveness of songs and in the last 2 we measure popularity because those two are the most important things we will need for the rest of the project.

## Datasets
Our internal goals for milestone two were to rate popularity and offensiveness.
We have analysed the datasets we have. Popularity can be represented by a "hotness" attribute in the million song dataset. Unfortunately, many entries are missing. Therefore we complemented it with information on how often each individual song was played. We don't know yet if we will use the Yahoo ratings information. The data we already have at our disposal seems sufficient for our analysis. Moreover the yahoo ratings don't map popularity to songs but to artists. We fear that this could distort our results. It might well be possible that a very popular artist has a few outliers in offensiveness (I think Rihanna has some collaborations with Eminem ?). An additional problem is that this dataset requires an authorization by Yahoo.

The size of the million song dataset is reported by the cluster to be over 200GB. Fortunately, we only work on small slices of that dataset, they proved to be rather conveniently partitioned. The data is split into a set of containers. Each container is a hdf5 file with well-documented components. We could select the subset of entries that are necessary and download them to our local computers. This condensed dataset is much smaller and fits well into memory, even on notebooks. We could use this to extract the hotness.
The hotness is a scalar between 0 and 1 and quantifies the popularity of a song. This metric would be just what we need to relate popularity and offensiveness. Unfortunately the measure is only defined for a small subset of songs.
Therefore we also included the _tasteprofile_ dataset which contains unique play counts by track ids. The popular appeal of a song should be directly reflected in the number of times it has been played. The tasteprofile is a simple table, size was not an issue.
Our third dataset, the MusixMatch lyrics database, offers an sqlite version of their data. It matches track ids to lyrics and has a size of just over 2GB. No cleaning was necessary to fit this into memory. In fact we could directly import the sqlite database into a pandas frame.
Rating the offensiveness of a song presents a challenge: We are no native speakers. Therefore we can't accurately judge the offensiveness of lyrics. We have searched the internet for existing compilations of offensive words and found a research project by the British telecommunications regulator Ofcom. They have established a list of swearwords, classified into different categories such as mild/medium/strong or discriminatory/non-discriminatory. We imported this data and applied it the lyrics from the MusixMatch dataset.

## Review
For milestone 2 we set the internal profile of quantifying offensiveness and popularity.
This has been done. So far we see no make significant changes to our plan.


# Plan for milestone 3

We revisited the goals that we advertised in our initial project idea. They are divided into two areas:
 - Analysing songs: Are there trends in offensiveness over time? Is there a correlation between offensiveness and popularity
 - Analysing lyrics: Can we identify "popular" or frequent swearwords? Can we see trends in the use of swearwords ?
 
For milestone 3 we want to focus on the first aspect: Analysing songs. 
Our basic idea is to use songs as a not censored record of colloquial phrases. This seems like the key aspect of our research. So we would like to invest as much time as possible into investigating and presenting our findings in this area. We consider the analysis of individual swearwords as a fallback plan. If (against our expectations) we can't find any strong trends in the dataset, we will reconsider the questions regarding lyrics.
 
 A first step will be to record correlations between the datasets that we have prepared: Correlations between offensiveness, time and rating. We will compile a range of visualizations. Then we will try to identify which of these tell the most interesting story.
