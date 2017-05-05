# Can Social Data Predict a Natural Catastrophe?

![image](https://media.giphy.com/media/CXLPSXYcP0mHe/giphy.gif)

## 13th April 2017 - Capstone, Part 1: Capstone Topic + Dataset Validation (Week 4)

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

## 5th May 2017 - Capstone Part 02! Problem Statement + EDA (Week 7)

<img src="wordcloud_hail_sample.png" alt="">

In this section of the capstone I will refine the problem statement and deliverables and perform an exploratory data analysis. 

Some specific goals of this project are to:

- Identify language in tweets that confirms a specific type of catastrophe is occuring (i.e.:hail)
- Identify language in tweets that suggests major damage to property or infrastructure is occuring
- Recognise sentiment in tweets that indiciates a severe event is occuring (extreme words such as "massive" or "terrifying")
- And ultimately... build a model that can effectively classify twitter data as being a catastrophic event..
- Stretch goal: a model that can be adapted to predicting catastrophes in real time

Success Criteria include:
- Effective processing the twitter data to identify the expected signatures (i.e.: key words such as 'hail', 'storm', 'damage'), indicating the type of event and how damaging/severe it is.
- Oberserving relationships and sentiment in the processed natural language of tweets.
- Identification of an algorithm, or combination of algorithms, that can accurately indicate/classify a catastrophic hail event from tweets.*

*Note that at this stage the target variables for classification are still under investigation.

### Project Methodology

### Data!!

Sifter is a service that provides search and retrieve access to every undeleted Tweet in the history of Twitter.
https://sifter.texifter.com/

For my project I purchased two datasets fro Sifter:

**Primary dataset: Brisbane Hail Storm** With the help of sifter, I performed the following search function to extract the data:

Rule: (contains hail OR storm OR damage OR flood OR insur OR "golf ball"~6 OR "tennis ball"~6 OR lightning OR thunder OR #brisbanehail OR #brisbanestorm OR "brisbane hail"~6 OR "brisbane storm"~6 OR #australiahail OR #australiastorm OR "australia hail"~6 OR "australia storm"~6 OR #auhail OR #austorm OR "au hail"~6 OR "au storm"~6 OR #qldhail OR #qldstorm OR "qld hail"~6 OR "qld storm"~6 OR #queenslandhail OR #queenslandstorm OR "queensland hail"~6 OR "queensland storm"~6 -(brisbane OR qld OR queensland OR australia OR au OR seqld) All duplicates removed.

This data query aims to capture all potential tweets that could relate to the identified hail event on 27th November 2014. I extracted 3 days worth of data however to begin with, I will only analyse a 24 hour period either side of the time the hail occured (15:00 - 17:00 AEDT) as I am primarily interested in the 'real-time' indicators.

As this event was a more widespread and had a higher insured loss, I will use this as my primary dataset for the EDA/model building (i.e.: my training data). The final dataset was delivered in csv format.

**Secondary dataset: Sydney Hail Storm** I performed a similar search in Sifter to gather data for a hail event in Sydney on 25th April 2015.

Rule: (contains hail OR storm OR damage OR flood OR "golf ball"~6 OR "tennis ball"~6 OR insur OR lightning OR thunder OR #sydneyhail OR #sydneystorm OR "sydney hail"~6 OR "sydney storm"~6 OR #australiahail OR #australiastorm OR "australia hail"~6 OR " australia storm"~6 OR #auhail OR #austorm OR "au hail"~6 OR "au storm"~6 OR #nswhail OR #nswstorm OR "nsw hail"~6 OR "nsw storm"~6 -(sydney OR nsw OR "new south wales" OR australia OR au) All duplicates removed.

This dataset will be used as my secondary data (i.e.: my test data). The final dataset was delivered in csv format.

**Supporting dataset: ICA Catastrophe Data 2016** This dataset was sourced from the Insurance Council of Australia (ICA). The Insurance Council of Australia collects catastrophe related claims data from the Australian market as part of its role in supporting the industry to deliver repairs, rebuilding and recovery services following large disasters. The ICA Catastrophe Database commenced in 1967 and records insurance loss estimates for declared insurance catastrophe events.

This dataset will be used as a reference for the two major hail events in 2014 and 2015. It will also serve as a useful guide for future events to investigate.

NLP:
I will use natural language processing techniques to analyse the actual tweet of each twitter record. Specifically I will use NLP to:
- remove regular expressions, tweet segmentation and other techniques (continued further in part-03 of capstone)
- perform word pattern matching and frequency analysis
- analyse sentiment of the tweets (later on in capstone).

Machine Learning:
Once I have determined the types of target (likely classifiers) I will need for my model, I will run through machine learning algorithms and modelling techniques and see which produces the optimal model. Some algorithms I have researched that may be best to use with NLP processed data are Naive Bayes, Logistic Regression, Decision Tress, Gradient Descent..? I will investigate and discuss the most appropriate methods further in part-03 of the captstone.

## Exploratory Data Analysis - Key Insights!

Some key insights from my EDA of the primary dataset of the Brisbane Hail twitter data include:

<img src="device_tweet_count.png" alt="">

**Twittascope!!??**
Taken from Twittascope website: "About Twittascope.com: Twittascope tweets authentic horoscopes for your Twitter account each morning. Provided by the Daily Insight Group, this leading horoscope service offers a daily dose of astrological insight."

This does not sound like a reliable resource for investigate tweets on natural catastrophes, so although this is a large sample of data we will exclude it from our project.

<img src="tweet_hail_frequency.png" alt="">

Signficiant spikes in the use of "hail" are observed in tweets at 6 - 8 AM GMT, which is 3 - 5PM Brisbane Daylight time. This corresponds with the known time of the major hail event in Brisbane. Another peak occurs later in the series - what could this relate to?

<img src="hail_sample_word_tweet_count.png" alt="">

The above graph shows the key words which are included within tweets that contain the word "hail" over the 24 hour period. Location information such as Brisbane and Australia are seen, as well as emotive words such as "massive, super, worst", all of which will be critical in my tweet classification process in the next phase of the capstone. Could "golf" and "ball" be related..?

### Next steps:

For the next stage of the Capstone I will refine the NLP processes already used in my EDA and continue to look at sub-groups of key words, investigate bi/tri grams and other relationships. I will then continue forward and investigate appropriate algorithms.

_Next Up... Part 3: Progress Report + Preliminary Findings: Week 9_
