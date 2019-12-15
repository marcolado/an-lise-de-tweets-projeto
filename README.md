# an-lise-de-tweets-projeto
import tweepy as tw
import pandas as pd 
import numpy as np
import seaborn as sb


auth = tw.OAuthHandler('Consumer_Key', 'Consumer_Secret_key')
auth.set_access_token('Consumer_Token', 'Consumer_Secret_Token')


api = tw.API(auth)
 redirect_url = auth.get_authorization_url()
 
 tuites = 'Bolsonaro' + '-filter:retweets'

class TweetAnalyzer():
    """
    Functionality for analyzing and categorizing content from tweets.
    """
    def tweets_to_data_frame(self, tweets):
        df = pd.DataFrame(data=[tw.text for tw in tweets], columns=['Tweets'])

       

        return df
        
        tweets=tw.Cursor(api.search, q=tuites).items(1000)
        
        tweet_analyzer = TweetAnalyzer()
        
        df = tweet_analyzer.tweets_to_data_frame(tweets)
        
        df.to_csv('bolsonarotuit')
