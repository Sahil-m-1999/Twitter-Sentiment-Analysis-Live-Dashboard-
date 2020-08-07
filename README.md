# Social Sentiment Dash Application
Live-streaming sentiment analysis application created with Python and Dash.
An integrated search bar is provided to input a word on which you need tweets.
The sentiments can be seen in the graphs updating in real time.
A sentiment of 0 indiactes neutrality. The range is from -1 (negative) to 1 (positive).
A pie chart also provides the ratio of positive to negative tweets.

![application example](https://pythonprogramming.net/static/images/dash/dashapplication.jpg)

## Repo Contents: 
- `dash_mess.py` - This is currently the main front-end application code. Contains the dash application layouts, logic for graphs, interfaces with the database...etc. Name is descriptive of the overall state of code :) ...this code is setup to run on a flask instance. If you want to clone this and run it locally, you will be using the `dev_server.py`
- `dev_server.py` - If you wish to run this application locally, on the dev server, run via this instead.
- `twitter_stream.py` - This should run in the background of your application. This is what streams tweets from Twitter, storing them into the sqlite database, which is what the `dash_mess.py` file interfaces with. 
- `config.py` - Meant for many configurations, but right now it just contains stop words. Words we don't intend to ever count in the "trending"
- `cache.py` -  For caching purposes in effort to get things to run faster. 
- `db-truncate.py` - A script to truncate the infinitely-growing sqlite database. You will get about 3.5 millionish tweets per day, depending on how fast you can process. You can keep these, but, as the database grows, search times will dramatically suffer. 

## Steps to run

- Clone repo
- install `requirements.txt` using `pip install -r requirements.txt`
- Fill in your Twitter App credentials to `twitter_stream.py`. There are 4 fields to fill. Go to [**apps.twitter.com**](https://apps.twitter.com/) to set that up if you need to.
- Run `twitter_stream.py` to build database
- While running the twitter_stream.py there may be some nltk libraries which may not be installed in your system so install those required modules of nltk if an error of nltk pops up.
- After twitter_stream.py is running succesfully a database will be created in the same directory of the files.
- If you're using this locally, you can run the application with the `dev_server.py` script.
- While running this file a flask instance website is generated in the prompt copy the web address and paste it in your browser to observe the complete application.
- You might need the latest version of sqlite(with fts5 support). 
```
sudo add-apt-repository ppa:jonathonf/backports
sudo apt-get update && sudo apt-get install sqlite3
```
- Consider running the `db-truncate.py` from time to time (or via a cronjob), to keep the database reasonably sized. In its current state, the database really doesn't need to store more than 2-3 days of data most likely. 


