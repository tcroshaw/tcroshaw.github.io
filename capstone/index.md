# Can Social Data Predict a Natural Catastrophe?

![image](https://media.giphy.com/media/CXLPSXYcP0mHe/giphy.gif)

## 13th April 2017 - Setting the Scene: A Catastrophic Twitter Analysis

_Project Introduction

The main objective of this project is to develop a model that can predict a natural catastrophe from social data. 

I will use natural language processing to analyse social posts and investigate which machine learning algorithms generate the most robust models to prove my hypothesis that language, volume and interconnectivity of social posts can indicate a significant catastrophe is occurring. 

The factors that determine a natural 'catastrophe', particularly from an insurance perspective, include financial/insurance loss, the number of claims or damage reports and the geographic extent. These will be the key indicators of catastrophic loss I hope to get from the model.

The study will focus on analysing **Twitter data** for major Australian **hail storm** events. I have selected two events for my analysis:

- Brisbane Hail Storm (27th November 2014): AUD 1,400m insurance loss
- Sydney Hail Storm (25th April 2015): AUD 400m insurance loss

I have chosen these events as they are two of the largest hail insurance losses since the age of Twitter and their catastrophic loss attributes (loss, claims and geography) are significantly different.

The specific goals of this investigation can be outlined in two main questions:
- Can twitter data detect hail events from the language people use in tweets?
- Can twitter data identify catastrophic hail events of differing severity?

To introduce you to my project, please follow the link to the slide deck of my 3 minute project pitch.

__[Capstone Part-01 Presentation](https://github.com/tcroshaw/GA_DSI_Capstone/blob/master/part-01/tom_part_01_presentation.pdf)__

This project was performed as part of General Assembley's Data Science Immersive Capstone. The initial deliverable was to choose a topic and problem, describing your goals & criteria for success, potential audience(s), and identifying 1-2 potential datasets. The format to present this information was a slide deck and Pecha Kucha format, 3 slides in 3 minutes! This was a lightning fast introduction to our project and it provided a valuable opportunity to train our thoughts into what the success criteria of our projects will be and how the analysis could be structured.

                                                   ***
                                                   
Now that the project is pitched, I will begin exploring my data further and report back with my findings.


------

## 5th May 2017 - Brisbane Hailstorm - A Preliminary Exploratory Data Analysis

<img src="wordcloud_hail_sample.png" alt="">

In this stage of the investigation I will refine the problem statement, deliverables and perform an exploratory data analysis on my main Twitter dataset, the Brisbane Hailstorm.

The specific goals of this project are to:

- Identify language in tweets that confirms a specific type of catastrophe is occuring (i.e.: a hail storm)
- Identify language in tweets that suggests damage to property or infrastructure is occuring as a result of the event
- Recognise sentiment in tweets that indiciates a _severe_ event is occuring (extreme words such as "massive" or "terrifying")
- And ultimately... build a model that can effectively classify tweets that indicate a catastrophic event...

*Note that at this stage the target variables for classification are still under investigation. Part-03 will refine my modelling approach...

## Project Methodology

### _Data!_

The historical twitter data were sourced from _Sifter_. Sifter is a service that provides search and retrieve access to every undeleted Tweet in the history of Twitter.

https://sifter.texifter.com/

For this project I obtained two datasets:

**Primary dataset: Brisbane Hail Storm** With guidance from Sifter, I performed the following search function to extract the data:

_Rule: (contains hail OR storm OR damage OR flood OR insur OR "golf ball"~6 OR "tennis ball"~6 OR lightning OR thunder OR #brisbanehail OR #brisbanestorm OR "brisbane hail"~6 OR "brisbane storm"~6 OR #australiahail OR #australiastorm OR "australia hail"~6 OR "australia storm"~6 OR #auhail OR #austorm OR "au hail"~6 OR "au storm"~6 OR #qldhail OR #qldstorm OR "qld hail"~6 OR "qld storm"~6 OR #queenslandhail OR #queenslandstorm OR "queensland hail"~6 OR "queensland storm"~6 -(brisbane OR qld OR queensland OR australia OR au OR seqld) All duplicates removed._

The data query aimed to capture all potential tweets that relate to the hail event on 27th November 2014. I extracted 3 days worth of data however I will only analyse a 24 hour period either side of the time the hail occured (15:00 - 17:00 AEDT) as I am primarily interested in 'real-time' indicators.

Because this event impacted a larger geographical area and produced a higher insured loss, I will use this as my primary dataset for the exploratory model development.

**Secondary dataset: Sydney Hail Storm** I performed a similar search in Sifter to gather data for a hail event in Sydney on 25th April 2015.

_Rule: (contains hail OR storm OR damage OR flood OR "golf ball"~6 OR "tennis ball"~6 OR insur OR lightning OR thunder OR #sydneyhail OR #sydneystorm OR "sydney hail"~6 OR "sydney storm"~6 OR #australiahail OR #australiastorm OR "australia hail"~6 OR " australia storm"~6 OR #auhail OR #austorm OR "au hail"~6 OR "au storm"~6 OR #nswhail OR #nswstorm OR "nsw hail"~6 OR "nsw storm"~6 -(sydney OR nsw OR "new south wales" OR australia OR au) All duplicates removed._

**Supporting dataset: ICA Catastrophe Data 2016** This dataset was sourced from the Insurance Council of Australia (ICA). "The ICA collects catastrophe related claims data from the Australian market as part of its role in supporting the industry to deliver repairs, rebuilding and recovery services following large disasters. The ICA Catastrophe Database commenced in 1967 and records insurance loss estimates for declared insurance catastrophe events." (ICA Wesbite)

This dataset will be used as a reference for the two major hail events in 2014 and 2015. It will also serve as a useful guide for future events to investigate.

Natural Language Processing:
I will use natural language processing techniques to analyse the actual tweet of each twitter record. Specifically I will use NLP to:
- Remove regular expressions, segment tweets and perform other cleaning operations (expanded in part-03 of project)
- Perform word pattern matching and frequency analysis
- Topic Clustering
- Analyse sentiment of the tweets (later on in Capstone).

Machine Learning:
Once I have determined the types of target I will need for my model, I will test classification algorithms and modelling techniques to observe which model produces the optimal results. Some  algorithms that are tradtionally good for text classification are Naive Bayes, Decision Tress and Stocatistic Gradient Descent. I will discuss the most appropriate methods further in part-03 of the blog.

## Exploratory Data Analysis - Key Insights!

Now that I have performed my preliminary EDA I will share some interesting observations of the 24-hour Brisbane Hail data...

<img src="device_tweet_count.png" alt="">

When investigating the devices used to produce these tweets I notice a strange source that produced the greatest number of tweets over the 24 hour sample.

**Twittascope!!??**

Taken from Twittascope website: "About Twittascope.com: Twittascope tweets authentic horoscopes for your Twitter account each morning. Provided by the Daily Insight Group, this leading horoscope service offers a daily dose of astrological insight."

This does not sound like a reliable resource for investigate tweets on natural catastrophes (!), so although this is a large sample of data it will exclude it from our project.

After I cleaned the data of all unreliable tweets, removed outliers and replaced null values, I investigated the frequency of the term 'hail' over the 24 hour period...

<img src="tweet_hail_frequency.png" alt="">

The above frequency distribution over the 24 hour period shows signficiant spikes in the use of 'hail' in tweets at 6 - 8 AM GMT, which is 3 - 5PM Brisbane Daylight time. This corresponds with the known time of the major hail event in Brisbane. Another peak occurs later in the series - what could this relate to? Was there another hail event elsewhere..?

Now we know the Brisbane hail event is strongly recognised in our data, what other terms are the most prevalent when this word was tweeted?

<img src="hail_sample_word_tweet_count.png" alt="">

The above graph shows the key words that were posted in tweets that contained the word 'hail'. Location information such as Brisbane and Australia are observed, as well as emotive words such as "massive, super, worst", all of which will be critical in the tweet classification process and sentinment analysis in later phases of the investigation.

_Could 'golf' and 'ball' be related..?_ It is common to associate hail size with objects, particularly common with objects such as "golf-ball" or "tennis-ball". I will therefore include a bigrams NLP investigation in later stages to see if this term is signficiant.

<img src="golf_ball_image.jpg" alt="">

### Next steps:

The next stage of the investigation will refine the NLP processes by continuing to look at groups of key words and investigate topic modelling. I will then trial different algorithms to .

---

## 17th May 2017 - NLP Continued, Preliminary Modelling and... Another Type of Catastrophe?

![image](https://media.giphy.com/media/fsMkxhVeKwGac/giphy.gif?response_id=591da0615bfef578251edb9f)

This update will outline the main results of the latest stage of the investigation and some critical feedback on my approach.

I have found that analysing text data is challenging, particularly Twitter data(!), but if performed correctly the results can be very powerful.

**Approach**

The approach to my analysis so far can be broken into four main sections

_Data Cleaning and Outlier Removal_

In my preliminary EDA I found that cleaning the user information was a significant step in improving the confidence of my records; identifying unreliable data sources (i.e.: Twittascope!) and cleaning the data was a very important step. The date information allowed me to plot the frequency of words over time and removing outliers ensures I exclude records that are potentially from misleading media or 'bots'.

I have now integrated the Sydney hail event and processed it with the Brisbane hail event in a single dataset. This ensures consitency in data engineering.

_Bag-Of-Words Exploratory Data Analysis:_

As previously discussed, tokenisation, stop-word removal and other natural language processing techniques are critical steps in this project. The output following these text cleaning exercises is a vectorised dataframe of all the key words used in tweets. Vectorisation also allows me to create targets for classification (i.e.: using the 'hail' word use as a class).

Analysis of this data has shown that within our sample there is clearly a skew of word counts to low frequency (as expected!) however there are some key words which are prevalent throughout tweet samples, which is likely due to the volume of tweets on specific subjects (i.e.: the hail events). 

Comparing the words that occur during the two events, especially over time, has been crucial in supporting my idea that twitter can identify natural catastrophes of significance... So much so that another type of event was recorded within my EDA!

<img src="top_words_corr.png" alt="">

The highest correlated words in my combined dataset (for both Brisbane and Sydney events) are: quake, hits, big and Nepal... We can now deduce that the twitter data also picked up another major natural catastrophe on this date: the Nepal Earthquake on 25th April 2015!

<img src="nepal_eq.jpg" alt="">

This additional discovery provides validation of the searching method, showing that this analysis can not only predict hail but also other natural disasters. This increases the scope of the project as well as potential future applications.

Geograhic Analysis:

<img src="map_hail_tweets.png" alt="">

A geographic analysis of the tweet data found a concentration in 'hail' tweets over Texas. Investigation found there was another hail event that also occurred on 25th April 2015 in San Antonio, causing hail storms of up to 2 inches. There is little evidence to suggest this was very damaging but could explain the rise in hail tweets in the latter hours of Cat_ID 154.

_LDA - Topic Modelling_

Latent Dirichlet Allocation, a type of statistical model for discovering abstract "topics" that occur in a collection of text records, has helped identify the core groupings of words in the data for our samples, as well as other significant topics within the data beyond these. Grouping the data by location and time has allowed powerful analysis of the key words that occur together; by narrowing the dataset into regions which are specific to the hail events, the key words indicating hail (and potential predictors) are more strongly recognised.

<img src="topic-modelling.png" alt="">

When performing the LDA on the full dataset, two other topics were identified (as above):
- 1. The Nepal Earthquake and 2. a very poor performance by the Melbourne Storm against the Manly Sea Eagles on 25th April 2015.
- Other events identified over these dates were the thanksgiving period in 2014 (and the associated poor travel weather!) and tweets concerning Boko Haram.

_Preliminary Algorithm Development_

Whilst modelling is still in its early phase, I have identified that classification algorithms will be the most appropriate for my text analysis. To begin with, I have investigated logisitic regression and decision tree classifications. I have selected key words indentified during the Bag-of-Words analysis and topic modelling to use as predictors and generated a hail 'class' as the target variable. My preliminary investigation looks at how well the Brisbane Hail data performs...

<img src="logregcoef.png" alt="">

Overall the decision tree classification model provides a slightly higher accuracy score than the logistic regression, the coefficients plotted on the bar graph above. Both models have coefficients of determination (R^2) of greater than 0.9 however only predict ~18% of our known positive hail classes. This indicates a more robust feature selection process (including a Principle Component Analysis) and further algorithm testing must next be performed to improve model performance.

**Lessons Learned from this stage of the project:**

- Dealing with null values and removing outliers appropriately are important however there is a trade-off between improving the distribution of a variable and knocking out too much data.
- The natural language processes and the sequence in which they are performed are very important when analysing text data, particularly 'messy' data such as tweets.
- The method of using key terms from Bag-Of-Words and topic modelling is useful for textual analysis and identifying common terms, however using this to limit the predictors in classification modelling potentially reduces the precision of the algorithm. Despite the high accuracy of our preliminary models, feature selection must be more robust to improve model performance.
- Other algorithms may be more appropriate for this project and further investigation will ensure the most effective machine learning methods are used.

***Next Steps***

1. More in-depth feature selection and Principle Component Analysis
2. Investigation of other classification models: Support Vector Machines, Naive Bayes and Random Forest in particular.
3. Sentiment analysis of the twitter data: do attitudes of tweets classify a natural catastrophe?

-----

## 6th June 2017 - Catastrophe Classification Models: Development and Results

<img src="hail_cloud.png" alt="">

This stage of the project brings together the analysis completed so far into a final delivery that includes sentiment analysis, a principle component analysis and a series of classification models.

***Sentiment Analysis***

Generally during very severe natural catastrophes, people tend to tweet emotive language to describe the events they're experiencing.

_Textblob_ is python library for processing textual data. The sentiment_analysis function returns the polarity score - a measure of the negativity, the neutralness, or the positivity of the text. This function was parsed over all tweets to understand how sentiment varied in for different catastrophe types.

<img src="sentiment.png" alt="">

The sentiment analysis results suggests that for the most extreme negative scores, the relative frequency of earthquake and (lesser so) hail tweets are greater than the 'all-tweets' distribution. The inverse is seen at positive sentiment scores.

Three major peaks are observed for negative scores at -0.25, -0.6 and -1.0 where either the hail or earthquake tweets exceed the frequency for all-tweet negative sentiment and in general, there are very few points where the negative sentiment of all tweets exceeds either catastrophe. This indicates the sentiment could be an indicator of catastrophic events and as such, this feature was integrated into the modelling.

Interestingly there appear to be more positive tweets for the earthquake event than for the hail events. This could be people tweeting to record their safety.

***Principle Component Analysis***

A Principle Component Analysis was performed to investigate whether a smaller number of uncorrelated variable represented a large amount of variance in the dataset and if I can reduce the multicolinearity by reducing the number of variables.
All word predictors (995 in total once locations and hail references were removed) were assessed in the principle component analysis to review the dimensionality.

The main conclusions of the PCA are:
- The maximum variance explained for any component is 1.2%, which is generally very low but considering the number of variables, it is fairly significant.
- The individual explained variance graph suggests every component explains some of the variance.

<img src="pca_components.png" alt="">

- The cumulative variation suggests that if we only wanted to retain 90% of the variance, ~800 components would still need to be retained in the modelling.
- When investigating the X's that contribute to the top-6 components, no single word (x) contributes significantly to the component's overall variance apart from PC1 and the word 'wolf'.

Little evidence suggests that removing principle components would signficantly reduce dimensionality enough to improve model performance, therefore all predictors were used in the final model development.

***Classification Algorithm Investigation***

#### 1. Hail Modelling 

A random forest classification algorithm was found to be the optimal model for the hail class target. The principle component analysis did not suggest that limiting components would be effective in reducing dimensionality, therefore all predictors (i.e.: words in the vectorised, normalised data) would be used in modelling. Whilst Naive Bayes, Stochastic Gradient Descent and Decision Trees all provided high accuracy score, their f1 scores were less than the ensemble random forest classifier, which was driven by the high recall value of the hail-class prediction (see ROC curve below for overall classification performance of each tested model). When the random forest classifier was optimised via gridsearching, the hyperparameters and fit with 100% of the data increased the recall to 0.82; a very positive result for the ability of tweets to predict hail.

<img src="roc_hail_models.png" alt="">

#### 2. Severity Modelling

When using the optimised model to train/test for each event, the classification results were very poor despite their high accuracy scores. This indicates that the tweets in each events use different language to communicate the hail. A subsequent classifiction analysis, using each event as class for a hail-only subset of the data, confirms this belief by producing moderately strong classification. It also produces common words used to describe severe events (chaos, slammed, worst) as the features with highest importance.

<img src="features_severity.png" alt="">

#### 3. Multiple Catastrophe Classification

A final analysis then introduced earthquake as a class with hail. This produced a high accuracy score of over 0.95 and strong classification metrics, particularly for earthquake. 

<img src="eq_report.png" alt="" width="400">

The moderate performance by hail in this model suggests that indepenent classification models for each natural peril will likely be optimal over a combined catastrophe classification. Further investigation is needed to determine how strong the earthquake classification performs alone.

---

### Project Conclusion

How well has this analysis delivered on our original goals?

#### Can twitter data detect hail events from the language people use in tweets?

The hail events were successfully identified at multiple stages in the analysis:
 - NLP successfully identifed words that relate to the hail events in question and record significant activity during the known time period of each event.
- Topic modelling identified strong clustering of words that relate to the hail events, particularly when subsets of the data were analysed specific to the time periods of each storm.
- Sentiment analysis recorded negative polarity of hails tweets exceeding the frequency of all-tweets. This aligns with the common trait for negative and extreme language during natural disasters.
- The hail modelling also produced a number of very promising results. The predictors were able to produce a random forest classification algorithm that accurately predicted 80% true positives of known positives when trained on the full dataset. The presicion and recall of the model increases with training size and with further samples for more types of hail events, it will likely improve further.

#### Can twitter data identify severe catastrophic hail events?

Knowing the impact of the Brisbane and Sydney hail events allowed us to draw some conclusions on how well language recognised more damaging catastrophes. There were a number of results that correctly indicate the severity of both events:
- NLP: Recognition of terms relating to severity within the NLP processes; specifically the bag-of-words analysis and topic modelling of each event.
- Training and testing the optimal hail model algorithm on each event. The poor ability to predict hail in each event suggests that is significant difference in the predictors that drive hail classification in each case.
- The event classification analysis produced strong results at predicting each again, reinforcing the difference between events. The predictors that drive this classifciation are words that indicate an extreme event such as _chaos, massive, super and slammed_.

##### Extension... Can twitter data identify other types of catastrophic events?

The discovery of the Nepal Earthquake was a positive confirmation of our search criteria and NLP process and allowed us to broaden the scope of the project into a third modelling investigation. The combination of earthquake with the hail class provided a promising result again, particularly for the earthquake classification had higher a f1 score than hail and the most positive class of all three. This suggests that tweets can very effectively recognise earthquake events without the term existing, likely due to such specific terminology commonly used for that type of disaster such as _magnitude and hits_.

---

***Stakeholder Recommendation and Next Steps***

The following recommendations will improve this analysis prior to model deployment:

1. Introduce more hail events to strengthen our classification model. More mid-tier events (i.e.: between the Sydney and Brisbane magnitude of loss) and more transitional events (<100M AUD) would allow us to make more confident conclusions about the terms driving the severe event classification.
2. Create a method that infers location from text and investigate clustering with known tweet location data. This would significantly improve the volume of corrdinates in the data and our knowledge of tweet locations.
3. Investigate sentiment analysis for the specific events - does polarity differ for more/less severe events?
4. Further algorithm analysis should be performed. This includes more intensive training/testing of data beyond the 50/50 split for the current algorithms and looking at others such as SVM.
5. Investigate other types of natural catastrophe. Earthquake was already identified but bushfires, floods and cyclones are also very common in Australia.
6. Also investigate alternative data sources could enhance this type of investigation. Text classification of facebook posts and image recognition of instagram posts are other potential social resources.

***Model Deployment:***
The following diagram outlines a potential deployment framework for the random forest classification model:

<img src="model_deployment.png" alt="">
Check back next week for the final presentation and closing words...

_[Back to Tom's Homepage](https://tcroshaw.github.io/)_
