# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & Classification


### Data Science Problem

Utilizing text collected from two different subreddits, this project seeks to predict the correct subreddit origin of a given post. Several processes will be used such as data acquisition via the Reddit API and natural language processing (NLP) methods, and various classification models will be implemented to analyze the performance results of each. The two subreddits chosen for this project were those pertaining to the ride-sharing companies Lyft and Uber. These were carefully chosen based on my genuine curiosity between the two companies, as they are practically interchangeable from a user perspective despite their vast and notable distinctions from a stakeholder perspective. An almost equal amount of posts were collected from each subreddit (701 from Lyft and 700 from Uber), primarily using only the post title and core text to train and test the models. The observations and insights gained from the data and models will be used to address business implications and recommendations for the respective companies.


## Executive Summary


### Contents:

This project is divided into the following various sections for step-by-step analysis:

•Data Science Problem Statement <br>
•Data Collection <br>
•Data Cleaning & EDA <br>
•Preprocessing & Modeling <br>
•Evaluation and Conceptual Understanding | Conclusion and Recommendations

### Data Dictionary
|          Name          |       Type       | Location            | Description                                                                                                                                           |
|:----------------------:|:----------------:|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| first_df               | pandas dataframe | Notebook 1          | Initial data from Lyft subreddits                                                                                                                     |
| second_df              | pandas dataframe | Notebook 1          | Initial data from Uber subreddits                                                                                                                     |
| count_df               | pandas dataframe | Notebook 2          | Dataframe specifically generated to analyze word count mean and distribution for each class                                                           |
| df                     | pandas           | Notebook 3          | Primary dataframe utilized for all preprocessing and modeling - consists of only 2 columns: text (object) and subreddit (indicating 'lyft' or 'uber') |
| lyft_uber              | csv file         | Datasets Folder     | Initial file saved with data collected from both subreddits                                                                                           |
| lyft_uber_all          | csv file         | Datasets Folder     | Second file saved after cleaning data, merging columns - called in as 'df' for all preprocessing and modeling                                         |
| model_1                | pkl file         | Datasets Folder     | File saved to alleviate kernel issues while generating coefficients from best performing model                                                        |
| top20words             | png file         | Images Folder       | Chart generated from another platform comparing the count distribution of the 12 words which were found in the top 20 list for both subreddits        |
| project_3_presentation | pdf file         | Presentation Folder | PDF version of deck shared during presentation                                                                                                        |


----

### Overview of performance of all 9 models:


| Model | Rank | Transformation Method | Classification Model | Test Score  | Train Score | Best CV Score    | AUC ROC   | Processing Seconds |   |
|-------|------|-----------------------|----------------------|-------|-------|-------|-------|---------|---|
| 1     | 1    | Count Vectorizer      | Logistic Regression  | 0.857 | 0.901 | 0.858 | 0.944 | 137.22  |   |
| 5     | 2    | TF-IDF                | Logistic Regression  | 0.855 | 0.852 | 0.856 | 0.929 | 86.52   |   |
| 4     | 3    | Count Vectorizer      | Random Forest        | 0.853 | 0.938 | 0.854 | 0.948 | 358.44  |   |
| 2     | 4    | Count Vectorizer      | KNN                  | 0.846 | 0.852 | 0.849 | 0.930 | 100.21  |   |
| 8     | 5    | TF-IDF                | Random Forest        | 0.839 | 0.941 | 0.854 | 0.946 | 78.45   |   |
| 3     | 6    | Count Vectorizer      | Naive Bayes          | 0.819 | 0.878 | 0.820 | 0.915 | 185.08  |   |
| 6     | 7    | TF-IDF                | KNN                  | 0.808 | 0.818 | 0.830 | 0.904 | 73.63   |   |
| 7     | 8    | TF-IDF                | Naive Bayes          | 0.789 | 0.848 | 0.821 | 0.903 | 7.36    |   |
| 9     | 9    | Count Vectorizer      | Logistic Regression  | 0.639 | 0.800 | 0.608 | 0.683 | 62.12   |   |

### Conclusions and Recommendations
Upon conducting some basic research into Uber and Lyft, it is very apparent that Uber has a substantial lead in many aspects. It was launched in March 2009, is available in 65 countries, averages 15 million rides per day, is valued at $72 billion, and has even expanded to include subsidiaries such as Uber Eats and Jump Bikes. On the other hand, Lyft arrived on the scene 3 years later (June 2012), is only available in the USA & Canada (with no current plans to spread to other countries), averages only 1 million rides per day, and is valued at $15 billion. Lyft also has ventured into new markets such as a "Minnie Van" service at Walt Disney World Resort as well as scooter & bike-sharing industries, however these also pale in comparison to Uber's expansion projects. 

However, based on the the results obtained with Model 9, it can be inferred that from a user perspective, Lyft and Uber are strikingly similar. Without the presence of the primary indicator of 'lyft' or 'uber' being included in the valid words upon which to make classification predictions, even the best model performed quite poorly in distinguishing whether a post came from the Lyft subreddit or the Uber one. Therefore, it seems that their key customers (drivers and riders) essentially tend to express very similar sentiments, whether it be complaints, questions, advice or sharing other general information.

Another notable statistic found during additinal research is that the average ride rating for Lyft is 4.8, compared to only 4.4 for Uber. Also, in terms of online participation via the Reddit platform, Lyft actually has 15.2k people in its 'community' while there are only 13.9k who have joined the Uber 'community'. Lyft is clearly still outperforming Uber in some arenas even though they could otherwise be considered the underdog of the two.

From a business perspective, I believe it would be the best interest for each company to take this information and these modeling techniques to better understand what their customers need and want. The benefit of Reddit is that is a completely netural platform (not generated or moderated by either company while as their respective Twitter, Facebook, and App ratings are), and this allows the contributors to post more genuine, authentic feelings. If Lyft and Uber don't do this already, I think it would be beneficial for each company to pay attention to these subreddits. The same data acquistition techniques could be used periodically in order to track changes in customer sentiments over time. Instead of using classification to determine the origin of the subreddit (which is already clear), a more powerful application of these techniques would be to classify each post based on who wrote it (rider or driver), the intended audience (rider/driver/company itself), and which type of post it is (complaint, question (such as app functionality or etiquette), advice, general information sharing, etc.). If organized and analyzed properly, the content provided in the subreddits could provide invaluable information for each company, allowing them to prevent problems, get ideas for new features, gain direct insight from their competitor's customers, and ultimately ensure that their own customers feel heard and valued, which is proven to be crucial for consumer retention.

----


### Additional Referenced Sources

http://www.businessofapps.com/data/uber-statistics <br>
http://www.businessofapps.com/data/lyft-statistics
