### Problem Statement

#### The objective of this project is to develop a text classification model that can accurately classify text posts from two different dating subreddits, namely "over30" and "over40." The aim is to distinguish between these two subreddits based on the textual content of the posts. By creating an effective classifier, we can provide valuable insights into the concerns, experiences, and preferences of individuals in the over 30 and over 40 age groups regarding dating, relationships, and related topics. This classification model will assist in identifying trends, patterns, and distinctive features specific to each age group, ultimately helping dating platforms and researchers better understand and cater to the needs and interests of these demographics.


[Data1](https://www.reddit.com/r/datingoverthirty/)
[Data2](https://www.reddit.com/r/datingoverforty/)

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**subreddit**|*category*|Reddit|Age over30 or Age over40|
|**title**|*category*|Extracted from Reddit|Title|
|**selftext**|*category*|Extracted from Reddit|Text|
|**title_length**|*int*|Reddit|Calcualted from title|
|**title_word_count**|*int*|Reddit|Calculated from title|

#### Data was extracted from reddit website using pushshift api 1000 rows at a time 8237 rows and 91 columns were extracted from subreddits over 30, 9921 rows and 91 columns were extracted from over40 subreddit. After concatenating and deleting duplicates I was left with 7666 rows, out of which only 2598 are from over forty

#### The mean legth of the title from over40 group  was less than the mean length from the over30 group.

#### Most title lengths fell between 10 and 70 and 75% of the word counts were below 12
#### Words like dating, date, relationship, advise are more popular from this data

### Conclusion

#### I've used four models to classify, firstly I used Countervectorizer with Naive Bayes Classifier, the model returned a training score of 0.77 and the testing score of 0.66. I then used Naive Bayes with TFIDF vecorizer, then I used two more models using support vector machine and xgboost classifier which returned the results below:


#### Training Score Counter Vectorizer Naive Bayes : 0.77
#### Testing Score Counter Vectorizer Naive Bayes : 0.66


#### Training Score TFIDF Naive Bayes : 0.74
#### Testing Score TFIDF Naive Bayes : 0.67

#### Training Score TFIDF SVM : 0.91
#### Testing Score TFIDF SVM : 0.67

#### Training Score CounterVectorizer, XGBoost Classifier : 0.75
#### Training Score CounterVectorizer, XGBoost Classifier : 0.66



#### All the models have more false positives except the one with Naive Bayes classifier using counter vectorizer, that model has less false positives than the other models but it has more false negatives. It is clear that the data is imbalanced. We need to find a way to balance the data by aquiring more data and analyzing emoji's and hashtags. The other reason why the models were not able to classify is because the vocaubulary used by both over30's and over40's is similar that is why it is important to find more data, balance the data and find clever ways like emoji's and hashtags to find the signals to differentiate.