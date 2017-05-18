# Can Social Data Predict a Natural Catastrophe?

![image](https://media.giphy.com/media/CXLPSXYcP0mHe/giphy.gif)

## 13th April 2017 - Setting the Scene: A Catastrophic Twitter Analysis

In Part 1 of the Capstone, the brief was to choose a topic and problem, describing your goals & criteria for success, potential audience(s), and identifying 1-2 potential datasets. 

The format to present this information is in a slide deck and Pecha Kucha format, 3 slides in 3 minutes! Whilst this was a lightning fast introduction to our project, it provided a valuable opportunity to train our thoughts into what the success criteria of our projects will be and how the analysis may be structured.

To introduce you to my project, please follow the link to the slide deck of my 3 minute project pitch.

[Capstone Part-01 Presentation](https://github.com/tcroshaw/GA_DSI_Capstone/blob/master/part-01/tom_part_01_presentation.pdf)


_Project Summary_

The main objective of this project is to develop a model that can predict a natural catastrophe from social data within a certain level of confidence. Following an exploratory data analysis, I will use natural language processing to analyse social posts and investigate which machine learning algorithms generate the most robust models to prove my hypothesis - that the language, volume and interconnectivity of social posts can indicate the a catastrophe's magnitude. 

The factors that determine the severity of these events, particularly from an insurance perspective, include  financial/insurance loss, the number of claims or damage reports and the geographic extent. These will be the key indicators of catastrophic loss I will hope to get from the model.

As it is not possible to analyse all catastrophe types within the period of the Capstone, I will focus on analysing **Twitter data** for major Australian **hail storm** events. I have selected two events for my analysis:

- Brisbane Hail Storm (27th November 2014): AUD 1,400m insurance loss
- Sydney Hail Storm (25th April 2015): AUD 400m insurance loss

I have chosen these events because they are two of the most significant hail storms from an insurance perspective during the age of Twitter, but their catastrophic loss attributes (loss, claims and geography) are significantly different.

Now that the project is pitched, I will begin exploring my data further and report back with my findings.  

------

## 5th May 2017 - Brisbane Hailstorm - A Preliminary Exploratory Data Analysis

<img src="wordcloud_hail_sample.png" alt="">

In this section of the capstone I will refine the problem statement, deliverables and perform an exploratory data analysis on my main Twitter dataset.

Some specific goals of this project are to:

- Identify language in tweets that confirms a specific type of catastrophe is occuring (i.e.: a hail storm!)
- Identify language in tweets that suggests damage to property or infrastructure is occuring as a result of the event
- Recognise sentiment in tweets that indiciates a _severe_ event is occuring (extreme words such as "massive" or "terrifying")
- And ultimately... build a model that can effectively classify tweets that indicate a catastrophic event..

I will evaluate the success of my project using the following criteria:

- I have effectively processed the twitter data to identify the expected signatures (i.e.: key words such as 'hail', 'storm', 'damage'), indicating the type of event and how damaging/severe it is.
- I can observe relationships and sentiment in the processed natural language of tweets.
- I have identified an algorithm, or a combination of algorithms, that can accurately indicate/classify a catastrophic hail event from tweets.*

*Note that at this stage the target variables for classification are still under investigation. Part-03 will refine my modelling approach...

### Project Methodology

### Data!!

I sourced my main datasets from _Sifter_. Sifter is a service that provides search and retrieve access to every undeleted Tweet in the history of Twitter.

https://sifter.texifter.com/

For my project I purchased two datasets:

**Primary dataset: Brisbane Hail Storm** With the help of sifter, I performed the following search function to extract the data:

_Rule: (contains hail OR storm OR damage OR flood OR insur OR "golf ball"~6 OR "tennis ball"~6 OR lightning OR thunder OR #brisbanehail OR #brisbanestorm OR "brisbane hail"~6 OR "brisbane storm"~6 OR #australiahail OR #australiastorm OR "australia hail"~6 OR "australia storm"~6 OR #auhail OR #austorm OR "au hail"~6 OR "au storm"~6 OR #qldhail OR #qldstorm OR "qld hail"~6 OR "qld storm"~6 OR #queenslandhail OR #queenslandstorm OR "queensland hail"~6 OR "queensland storm"~6 -(brisbane OR qld OR queensland OR australia OR au OR seqld) All duplicates removed._

This data query aims to capture all potential tweets that could relate to the identified hail event on 27th November 2014. I extracted 3 days worth of data however to begin with, I will only analyse a 24 hour period either side of the time the hail occured (15:00 - 17:00 AEDT) as I am primarily interested in the 'real-time' indicators.

As this event was a more widespread and had a higher insured loss, I will use this as my primary dataset for the EDA/model building (i.e.: my training data).

**Secondary dataset: Sydney Hail Storm** I performed a similar search in Sifter to gather data for a hail event in Sydney on 25th April 2015.

_Rule: (contains hail OR storm OR damage OR flood OR "golf ball"~6 OR "tennis ball"~6 OR insur OR lightning OR thunder OR #sydneyhail OR #sydneystorm OR "sydney hail"~6 OR "sydney storm"~6 OR #australiahail OR #australiastorm OR "australia hail"~6 OR " australia storm"~6 OR #auhail OR #austorm OR "au hail"~6 OR "au storm"~6 OR #nswhail OR #nswstorm OR "nsw hail"~6 OR "nsw storm"~6 -(sydney OR nsw OR "new south wales" OR australia OR au) All duplicates removed._

This dataset will be used as my secondary data (i.e.: my test data).

**Supporting dataset: ICA Catastrophe Data 2016** This dataset was sourced from the Insurance Council of Australia (ICA). "The ICA collects catastrophe related claims data from the Australian market as part of its role in supporting the industry to deliver repairs, rebuilding and recovery services following large disasters. The ICA Catastrophe Database commenced in 1967 and records insurance loss estimates for declared insurance catastrophe events." (ICA Wesbite)

This dataset will be used as a reference for the two major hail events in 2014 and 2015. It will also serve as a useful guide for future events to investigate.

Natural Language Processing:
I will use natural language processing techniques to analyse the actual tweet of each twitter record. Specifically I will use NLP to:
- remove regular expressions, tweet segmentation and other techniques (continued further in part-03 of capstone)
- perform word pattern matching and frequency analysis
- analyse sentiment of the tweets (later on in capstone).

Machine Learning:
Once I have determined the types of target (likely classifiers) I will need for my model, I will run through machine learning algorithms and modelling techniques and see which produces the optimal model. Some algorithms I have researched that may be best to use with NLP processed data are Naive Bayes, Logistic Regression, Decision Tress, Gradient Descent..? I will investigate and discuss the most appropriate methods further in part-03 of the captstone.

## Exploratory Data Analysis - Key Insights!

Now that I have performed my preliminary EDA I will share some key insights of the 24 hour Brisbane Hail twitter data...

<img src="device_tweet_count.png" alt="">

When investigating the devices used to produce these tweets I notice a term that produced the greatest number of tweets over the 24 hour sample.

**Twittascope!!??**

Taken from Twittascope website: "About Twittascope.com: Twittascope tweets authentic horoscopes for your Twitter account each morning. Provided by the Daily Insight Group, this leading horoscope service offers a daily dose of astrological insight."

This does not sound like a reliable resource for investigate tweets on natural catastrophes (!), so although this is a large sample of data we will exclude it from our project.

After I cleaned the data of all unreliable tweets, I investigated the frequency of the term "hail" over the 24 hour period...

<img src="tweet_hail_frequency.png" alt="">

The frequency distribution over the 24 hour period shows signficiant spikes in the use of word "hail" in tweets at 6 - 8 AM GMT, which is 3 - 5PM Brisbane Daylight time. This corresponds with the known time of the major hail event in Brisbane. Another peak occurs later in the series - what could this relate to? Was there another hail event globally?...

Now we know they key event type is recognised in our data, what other terms are the most prevalent when this word was tweeted?

<img src="hail_sample_word_tweet_count.png" alt="">

The above graph shows the key words which are tweeted  at the same time as the word "hail". Location information such as Brisbane and Australia are observed, as well as emotive words such as "massive, super, worst", all of which will be critical in my tweet classification process in the next phase of the capstone. 

_Could "golf" and "ball" be related..?_ It is common to associate hail size with objects, particularly common with objects such as "golf-ball" or "tennis-ball". I will therefore include a bigrams NLP investigation in the next stage of the capstone to see if this term is signficiant and more are picked up.

<img src="golf_ball_image.jpg" alt="">

### Next steps:

For the next stage of the Capstone I will refine the NLP processes already used in my EDA and continue to look at sub-groups of key words, investigate bi/tri grams and other relationships. I will then investigate potential appropriate algorithms to use in the model development.

## 17th May 2017 - NLP continued, preliminary modelling and another type of catastrophe..?

![image](https://media.giphy.com/media/fsMkxhVeKwGac/giphy.gif?response_id=591da0615bfef578251edb9f)

This update will provide details of the key insights I have gathered during the latest stage of this investigation and some critical feedback on my approach so far.

I have found that analysing text data is challenging, particularly Twitter data(!), but if performed correctly the results can be very powerful.

***Approach**

My approach to continuing my analysis can be broken down into four main sections

_Data Cleaning and Outlier removal_

In my preliminary EDA I found that cleaning the user information was a significant step in improving the confidence of my records; identifying useless data sources (i.e.: Twittascope!) and cleaning the data was a very important step. The date information also me to plot the frequency of words over time and removing outliers (of numeric user variables) ensures I remove records that are potentially misleading from media or 'bots'.

I have now integrated the Sydney hail event and processed this and the Brisbane hail event in a single dataset. This ensures consitency in data munging and easier analysis grouping.

_Bag-Of-Words Exploratory Data Analysis:_

Using tokenisation, stop-word removal and other natural language processing techniques are critical steps for this project. The output of which is a vectorised dataframe of all the key words used in tweets. Vectorisation also allowed me to create targets for classification (i.e.: using the 'hail' word use as a class).

Analysis of this data has shown that within our sample, there is clearly a skew of word counts to low frequency (as expected!) however there are some key words which are prevalent throughout the tweets due to the volume of tweets on that subject (i.e.: the hail events). 

Comparing the words that occur during the two events, especially over time, has been crucial in supporting my idea that twitter can identify natural catastrophes... So much so that another type of event - Nepal Earthquake - was recorded within my EDA!

<img src="top_words_corr.png" alt="">

The highest correlated words in my combined dataset (for both Brisbane and Sydney events) are: quake, hits, big and Nepal... We can now deduce that the twitter data also picked up another major natural catastrophe on this date: the Nepal Earthquake!
The additional discovery of the earthquake event provides validation of the searching method, showing that this analysis can not only predict hail but also other natural disasters. This increases the scope of the project as well as potential future applications.

_LDA - Topic Modelling_

Latent Dirichlet Allocation, a type of statistical model for discovering the abstract "topics" that occur in a collection of documents, has helped identify the core groupings of words in the data for our events, as well as other major topics within the data beyond these. Grouping the data by location and time has allowed a powerful analysis of the key words that occur together; by narrowing the dataset into regions which are specific to the hail events, the key words (and potentially predictors) indicating hail are more strongly recognised.

Beyond the hail event, other topics that were identified in the LDA include thanksgiving (and associated poor travel conditions!), boko haram and a very poor performance by the Melbourne Storm against the Manly Sea Eagles.

_Preliminary Algorithm Development_

Whilst modelling is still in its early stage, I have identified that classification algorithms will be the most appropriate for my text analysis. To begin with, I have investigated logisitic regression and decision tree classifications. I have selected key words indentified during the Bag-of-Words analysis and topic modelling to use as predictors and generated a hail 'class' as the target variable.

<img src="logregcoef.png" alt="">

Overall the decision tree classification:...
...
...

**Lessons Learned:**

- Dealing with null values removing outliers appropriately is important however there is a trade-off between improving the distribution of a variable and knocking out too much data.
- The natural language processes and the sequence in which they are performed are very important when analysing text data, particularly 'messy' data such as tweets.
- The method of using key terms from Bag-Of-Words and topic modelling is useful for textual analysis and identifying common terms, however limiting the predictors in classification modelling limits the success of the algorithms. Despite the high accuracy of our models, feature selection must be more robust to improve model performance.
- Other algorithms may be more appropriate for this project and further investigation will be needed to ensure the correct machine learning methods are used.

***Next Steps***

1. More in-depth feature selection and principle component analysis
2. Investigation of other classification models
3. Potentially a sentiment analysis of the twitter data: do attitudes of tweets classify a natural catastrophe?
