# Example Twitter API data collection using Tweepy
import tweepy

consumer_key = 'YOUR_CONSUMER_KEY'
consumer_secret = 'YOUR_CONSUMER_SECRET'
access_token = 'YOUR_ACCESS_TOKEN'
access_token_secret = 'YOUR_ACCESS_TOKEN_SECRET'

auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)

api = tweepy.API(auth)

# Collect tweets
tweets = api.search(q='your_search_query', count=100)
import re

def preprocess_text(text):
    # Remove URLs
    text = re.sub(r'http\S+', '', text)
    # Remove special characters and numbers
    text = re.sub(r'[^a-zA-Z\s]', '', text)
    # Convert to lowercase
    text = text.lower()
    return text

cleaned_tweets = [preprocess_text(tweet.text) for tweet in tweets]
from textblob import TextBlob

def get_sentiment(text):
    analysis = TextBlob(text)
    if analysis.sentiment.polarity > 0:
        return 'Positive'
    elif analysis.sentiment.polarity == 0:
        return 'Neutral'
    else:
        return 'Negative'

sentiments = [get_sentiment(tweet) for tweet in cleaned_tweets]
import matplotlib.pyplot as plt
import seaborn as sns

# Create a sentiment distribution plot
sns.countplot(sentiments)
plt.xlabel('Sentiment')
plt.ylabel('Count')
plt.title('Sentiment Analysis of Social Media Data')
plt.show()

# Calculate sentiment statistics
positive_count = sentiments.count('Positive')
neutral_count = sentiments.count('Neutral')
negative_count = sentiments.count('Negative')


