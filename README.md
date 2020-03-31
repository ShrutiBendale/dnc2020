# Studying the 2020 DNC Primary elections and discussions of it on Twitter
* Collected and preprocessed over 2 billion tweets over the course of two months using the Twitter streaming API.
* Performed sentiment analysis on the tweets and provided insights like the progression of overall sentiment about a candidate over a month, daily trending hashtags and mentions using graphs and visualization tools.

<p align="center"><img src = "https://shrutibendale.files.wordpress.com/2020/03/2560px-united_states_senate_elections_2020.svg_.png" width = "500"></p>

<br>Tweets are being streamed using the Twitter Streaming API. We tracked keywords, mentions and hashtags mapped to all candidates, from the Democratic party, running for 2020 presidential election. (See keywords.txt for a list of the keywords we used for each candidates)
The streams are delivered in compressed Gzip format. 



## 1.SeperatingByDates.ipynb 
Seperates tweets according to dates and creates seperate dictionaries for all dates. These dictionaries are saved as pickle files in the 'Processed Tweets' folder and each contains all the tweets on that day.

#### Format of each dictionary: <br>
key =>tweet_id, value => {created_at: "", tweet_id: "", user_id: "", tweet_text: "", hashtags: "", user_mentions: ""}

#### Example from the dictionary for  Mar 19,2020: <br>

1240672375345156096: <br>
{'created_at': 'Thu Mar 19 16:11:59 +0000 2020',<br>
'tweet_text': 'the fact that Bernie Sanders doesn’t give a single shit about his status in the election and is instead ONLY concerned about the pandemic should tell you everything you need to know about what his presidency would be like.',<br>
'id': 1240672375345156096,<br>
'user_id': 906327160520155136,<br>
'hashtags': [],<br>
'user_mentions': []},<br>

 1240672375600902144: <br>
{'created_at': 'Thu Mar 19 16:11:59 +0000 2020',
'tweet_text': 'This poor man is going to die tryna save America while y’all hardly paying him any mind. FEEL THE BERN‼️',
'id': 1240672375600902144,<br>
'user_id': 527157011,<br>
'hashtags': [],<br>
'user_mentions': []},...<br>

  

## 2.SentimentAnalysis.ipynb
Uses the VADER sentiment analysis library to calculate the sentiment score for each tweet. It adds this score to the dictionary of each tweet as a 'sentiment' tag.

#### The above example after being processed by the sentiment analysis script:<br>
1240672375345156096: <br>
{'created_at': 'Thu Mar 19 16:11:59 +0000 2020',<br>
'tweet_text': 'the fact that Bernie Sanders doesn’t give a single shit about his status in the election and is instead ONLY concerned about the pandemic should tell you everything you need to know about what his presidency would be like.',<br>
'id': 1240672375345156096,<br>
'user_id': 906327160520155136,<br>
'hashtags': [],<br>
'user_mentions': [],<br>
<b>'sentiment': 0.2732},</b><br>

1240672375600902144: <br>
{'created_at': 'Thu Mar 19 16:11:59 +0000 2020',<br>
'tweet_text': 'This poor man is going to die tryna save America while y’all hardly paying him any mind. FEEL THE BERN‼️',<br>
'id': 1240672375600902144,<br>
'user_id': 527157011,<br>
'hashtags': [],<br>
'user_mentions': [],<br>
<b>'sentiment': 0.5859}</b>,...<br>



## 3.PerDayAnalysis.ipynb 
Identifies the candidates associated with each tweet, for all dates and creates a dataframe to keep a track of number of tweets and sentiment for all candidates for all the dates.
'daily_candidate_sentiments_df.pkl' and 'daily_candidate_tweets_df.pkl' are the dataframes created after processing approx. 2 billion tweets.

#### Sample dataframe for "number of tweets per candidate" for 5 days:
![count df](https://shrutibendale.files.wordpress.com/2020/03/sentiment_df.png)

#### Sample dataframe for "sentiment per candidate" for 5 days:
![sentiment df](https://shrutibendale.files.wordpress.com/2020/03/count_df.png) 


## 4.Graphs.ipynb
Plots these dataframes to graphs that shows the sentiment for a candidate over time and the number of tweets per candidate over time.<br>

![sentiment graph](https://shrutibendale.files.wordpress.com/2020/03/sentiment_graph-1.png)
![tweets graph](https://shrutibendale.files.wordpress.com/2020/03/tweets_graph-1.png)




