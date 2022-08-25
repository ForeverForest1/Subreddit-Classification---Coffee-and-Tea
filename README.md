**Project 3: Reddit Posts Classification**

Background and Problem Statement:
Social media offers a real-time platform for food and beverage (F&B) businesses to engage with their customers, even those not within their immediate vicinity. These social media interactions can provide a wealth of insights to help F&B business owners improve their businesses. However, for the many small business establishments, managing and responding effectively to customer posts can be challenging.

Working as an analyst for an F&B consultancy, you are tasked with developing a model that can sort a text post by whether it is about tea or coffee. The target clients are cafe operators, with the aim of the model being to help business owners better manage their social media interactions, as well as derive quick insights about their customers. This project will use data scraped from the subreddits for tea and coffee, and using it to train a model that can predict which subreddit a post came from. This is used as a proxy to assess the model's ability to determine whether a text post is about coffee or tea.

The tea and coffee subreddits can be found below:

https://www.reddit.com/r/tea/
https://www.reddit.com/r/Coffee

Overview of Approach:
The scraped posts were cleaned, processed and used to train four modeling pipelines. Each pipeline is made up of 1 vectoriser and 1 classifier. Two vectorisers and classifiers were tested in this project. 

The two vectorisers used are: i) CountVectorizer and ii) Term Frequency–Inverse Document Frequency (TF-IDF) Vectorizer
The two classifiers used are: i) Multinomial Naive Bayes and ii) Logistic Regression

GridSearchCV was used to optimise the hyperparameters, train and score the four models.The best model was chosen based on the highest accuracy score from the test data. The chosen model was used to derive the top 10 words which had a higher likelihood to predict which subreddit a post came whether it is from r/tea or r/Coffee.

Summary of Findings:

**Chosen model** - `TF-IDF + Multinomial Naive Bayes` was chosen as our best model as it had the highest accuracy score of 0.931 based on the test score. The model also exhbited high AUC ROC and good classification metric values, well above our baseline accuracy of 0.602 which was simply based on which subreddit the majority of posts came from.
**Good performance from all models** - All 4 modeling pipes produced relatively high accuracy scores (lowest 0.896, highest 0.931) and AUC ROC (lowest 0.96, highest 0.976) within a tight range, with similarly good classification metrics.
**Naive Bayes outperforms Logistic Regression** - The two models with Naive Bayes classifiers had higher accuracy scores than the Logistic Regression models. This is likely due to the mutually exclusive nature of tea and coffee drinkers, which increases the independence of the variables and hence effectiveness of Naive Bayes models.
**Difference in categories of top predictor words** - Top predictor words for tea tend to describe variety and quality of tea, while the words for coffee tend to be related to equipment and technology involved in making coffee.

Data Dictionary:
The following three columns were used from the scraped Reddit posts:

|Feature|Type|Description|
|:---|:---:|:---:|
|subreddit|str|subreddit that the post was from|
|selftext|str|body of text in the post|
|title|str|title of the pos|
