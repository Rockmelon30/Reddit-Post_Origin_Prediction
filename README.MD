# Project 3: Reddit Scraping 

# Problem Statement

Can we build a model that is able to tell the subreddit origin of a given post between two subreddits?

# Questions

1. Can we accurately predict the subreddit of origin of a given post between r/nutrition and r/fitness?
2. How will success be measured?
3. How accurate of a model can we build and how could it be improved upon?

# Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**Title**|*string*|All|The title of the associated post.|
|**ID**|*string*|All|The unique ID given to a post by Reddit.|
|**Author**|*string*|All|User who created post.|
|**URL**|*string*|All|URL of the Reddit post.|
|**Score**|*int*|All|Balance of upvotes/downvotes.| 
|**Comment Count**|*int*|All|The number of comments on the post.|
|**Created**|*float*|All|Date of post creation.|
|**Subreddit**|*string*|All|Subreddit of origin.|



## Data Used
1. fitness_scrape_1.csv
2. fitness_scrape_2.csv
3. fitness_scrape_3.csv
4. fitness_scrape_year.csv
5. fitness_scrape_month.csv
6. fitness_scrape_new.csv
7. fitness_scrape_controversial.csv
8. nutrition_scrape_1.csv
9. nutrition_scrape_2.csv
10. nutrition_scrape_3.csv
11. nutrition_scrape_year.csv
12. nutrition_scrape_month.csv
13. nutrition_scrape_new.csv
14. nutrition_scrape_controversial.csv
15. reddit_posts.csv
16. reddit_posts_tokenized.csv


Links to outside resources used:
1. Fitness subreddit: https://www.reddit.com/r/Fitness/
2. Nutrition subreddit: https://www.reddit.com/r/nutrition/
3. Reddit PRAW API: https://www.reddit.com/prefs/apps
4. PRAW Documentation: https://praw.readthedocs.io/en/latest/code_overview/models/subreddit.html#praw.models.Subreddit.top


---

## Requirements
- Python, Jupyter
- Pandas, Numpy, Matplotlib
- Scikit Learn Libraries:
   - StandardScaler, Train Test Split, Metrics, LogisticRegression
   - CountVectorizer, TfidfVectorizer
   - Pipeline, MultinomialNB
- Nlkt Libraries:
   - PorterStemmer, WordNetLemmatizer
   - stopwords, wordnet
   - word_tokenize, sent_tokenize, RegexpTokenizer

---
## Executive Summary
 The project aims to leverage machine learning techniques to distinguish between posts originating from two popular subreddits: fitness and nutrition. By scraping data from these subreddits and building predictive models, the goal is to accurately classify which subreddit a given post belongs to, based on its content.
 
#### Objectives
1. Data Collection: Scrape posts from the fitness and nutrition subreddits to create a comprehensive dataset for analysis.
2. Data Processing: Clean and preprocess the text data to ensure it is suitable for model training.
3. Model Development: Develop and train machine learning models to predict the subreddit of origin for each post.
4. Evaluation: Assess the performance of the models using various metrics to ensure their accuracy and reliability.


#### Methods
  - Initialized PRAW API on Reddit
  - Decided on two subreddits among top 1% of subreddits (r/Fitness and r/Nutrition)
  - Scraped data over the course of several days, as well as by month, year, top, new and controversial
  - Explored data for missing values and outliers
  - Combined all scraped data into larger dataframes based on subreddit
  - Added column to fitness and nutrition dataframes based on subreddit of origin for model prediction use
  - Created a function that would return a new column that was tokenized, lemmatized, lowercase, and removed punctuation and stop words
  - Examined most common tokens among my two dataframes
  - Combined nutrition and fitness dataframes
  - Determined baseline accuracy
  - Created CVEC and TF-IDF based models
  - Examined most frequent words among my incorrect predictions
  - Tried using GridSearch, bigrams and trigrams to see if they would produce a better model
  

#### Findings
  - The logistic regression model demonstrated a high level of accuracy in predicting the subreddit of origin for a given post. Cross-validation confirmed the model's generalizability and reliability.
  - Analysis of the model revealed that certain keywords and phrases were strong indicators of the post's subreddit, highlighting the distinct linguistic characteristics of fitness and nutrition discussions.
  - My best model was the CVEC based model as it had nearly the highest test score among my models but less variance.
  - Using bigrams and trigrams increased my testing score mildly but also introduced more variance between my train and test scores.

#### Next steps
  -   If I were to continue working on improving my model, I might try removing a portion of the most common words among my incorrect predictions to see if it improved my models
  -   I might also try using forest type models
  -   I'd also try neural networks once I've had a chance to study them
