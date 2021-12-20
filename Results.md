---
layout: full
altair-loader:
  altair-chart-1: "charts/bestnounsALT_newpol.json"
hv-loader:
  hv-chart-1: ["charts/measlesHvplot.html", "500"] # second argument is the desired height
folium-loader:
  folium-chart-1: ["charts/foliumChart.html", "400"] # second argument is the desired height
  folium-chart-2: ["charts/percent_no_internet.html", "400"] # second argument is the desired height
LDA-loader:
  LDA-chart-1: ["charts/rall_best_ldamodel.html", "600"]
---
## big chagne BIG FRICKEN CHAGENES

# A Look at Reddit's Values, IRL Events, and Possible Bad Actors
*Gianluca Mangiapane, Bri Cervantes*


## Question We Set Out to Answer, and the Ones We Actually Did

#### 1. What does Reddit Value? What are the common characteristics/patterns in top r/all posts?

Given Reddit's self-defined culture, we wanted to first investigate what users on Reddit value. While we know that Reddit is home to countless sub-cultures, our approach focused on indentifying the overarching culutre of Reddit. What becomes the most popular? R/all is the front page of Reddit and is where all the most popular posts end up. It collects posts from subreddits across that platform that agree to participate and represents the majority rule of Reddit. 

In seeking to find out more about what gets popular, we pulled roughly 2,5000 top posts from r/all sorted by best of all time. We wanted to know if what is popular is positive or negative, whose posts are becoming popular and by extension if there are a small group of people that dominate the r/all space. Similarly, we were interested in where the popular posts are coming from, are there a small group of subreddits that dominate r/all. Further, we attempted to identify common themes between the posts. 

We first took a quick look at possible superusers; users with posts that ended up on the top of r/all more than 10 times, and super-subreddits; subreddits where more than 50 posts in our sample originated from. There were plenty in both categories. We should note that at least one the users on the top graph is u/DeepF*ckingValue, the claimed leader of the wallstreet takeover by reddit users on r/WallStreetBets. 

[![common users and subreddits on r/all](/KarmaMine/assets/img/Common.png)](/KarmaMine/assets/img/Common.png)


Next, we investigated the general sentiment of these posts and associated them with the subreddits they came from. To do so we used TextBlob, which provided polarity and subjectivity ratings. When we noticed some odd results we experimented with another NLP, Flair. Below are the results showing polarity ratings from Flair and Textblob, as well as sentiment ratings from only Textblob. The graph below shows the sentiment for all of the posts we pulled from r/all grouped by the subreddit they came from. (Click on the image to open it in a new tab and zoom in.)

[![sentiment, polarity by subreddit from posts on r/all](/KarmaMine/assets/img/subdotplot_newpol.png)](/KarmaMine/assets/img/subdotplot_newpol.png)

It's clear even by the name of some subreddits what the polarity rating might be. For example, r/wholesomememe trends positive under Textblob and Flair polarity rating, while r/wellthatsucks was rated very negative by Flair and only slightly negative by Textblob. Another way to examine general polarity of the posts we captured is to inspect the most frequent noun phrases. The interactive plot below shows a list of the top 100 most common noun phrases maped with their polarity determined by Flair on the left. 

<div id="altair-chart-1" style= "width: 400px;"></div>

Finally, we attempted to identify some common themes in the posts that we pulled from r/all. Using the Gensim library we employed a topic model to extract common themes in the noun phrases extracted from the titles by again using Textblob. With the [help of examples published by Data Science With Raghav](https://github.com/raaga500/YTshared/blob/master/V4_TopicModelling_4.ipynb) we identified roughly 20 clusters of potential themes. Below is an interactive chart that shows on the top 10 words in each topic cluster on the right. On the left is a intertopic distance map, that in very simple terms shows the relative 'distance' between the topics identified. Circles that are closer together represent topics that are more related to each other than circles far apart. Additionally the size of the cirlces represent the number of words associated with each topic. Though we've elected to only show the top 10 words associated with each topic, some topics include over 30 keywords. 

This visualization was first developed by [Carson Sievert and Kenneth E. Shirley.](https://nlp.stanford.edu/events/illvi2014/papers/sievert-illvi2014.pdf), and more details about how to interpret it can be [found on alteryx.com](https://community.alteryx.com/t5/Data-Science/Getting-to-the-Point-with-Topic-Modeling-Part-3-Interpreting-the/ba-p/614992).

<div id="LDA-chart-1"></div>

this is the iframe code below
<iframe src="charts/rall_best_ldamodel.html" frameborder="0" id="mainPageBody" width="1080px" height="1080px"></iframe>

If you find this chart confusing, you're not alone. We believe that the visual representation is very clear, but what exactly the topics are is not. Further we believe that this is a result of the data and the nature of Reddit. As shown in the bar graphs of common subreddit featured on r/all, the top two most common subreddits are r/pics and r/memes. These are two image based subreddits and, from our experience as reddit users, we can assume that the titles associated with image posts may not be all that illuminating of what the context of the post is. Additionally, Reddit is a very weird place, where platform-wide inside jokes abound. While our knowledge of natural language processing is limited, we think it's safe to say that the LDA model we employed could not have been expected to pick up on the nuances of Reddit's jokes. 


#### 2. How representative is Reddit’s front page of what’s happening in the world? 


While Reddit is a subculture unto itself ([ex.1](https://www.reddit.com/r/Music/comments/56cdgm/ama_im_really_rick_astley_i_swear_and_to/), [ex.2](http://i0.kym-cdn.com/entries/icons/original/000/016/212/manning.png)), it’s not possible for the platform to fully extricate itself from the rest of the IRL world. As a result, its lively subculture not only amplifies reddit-wide values, but it can also act as an accelerant for ideas and narratives that have context outside of Reddit. Further, the loyalty that users have to the site, might mean they use it for more than just fun. In 2016, the Pew Research Center found that 78% of Reddit users get their news from the site.[^5] We’ll investigate the connections that recent r/all posts have with news headlines by identifying if they share common themes. Additionally, we’ll compare sentiment analysis results from posts and news headlines to investigate if general feelings are shared across platforms.

#### 3. How does Reddit impact the real world? AKA why does understanding Reddit matter?

It’s clear the IRL world can influence what people talk about on Reddit, but can small actors use Reddit to steer larger narratives? Last year’s rise of r/WallStreetsBets (WSB) exposed the nation to the reality-creating power of Reddit. We all watched, or maybe even participated, as the subculture of WSB spilled out over the stock market, turning internet ideas into IRL impacts. But given that Reddit is open to anyone and typically promotes user anonymity, anyone can harness the platform’s culture-shifting power with the right resources. In addition to our cluster analysis of both r/all posts and news headlines, we hope to identify features that may be associated with documented qualities of robot users. Similarly, we’ll investigate posts and comments for signs of (bad) robot activity. Further, if our analysis in the previous steps identifies superusers and super subreddits, we’ll explore the common themes of their posts and users activity to draw some conclusions about whether they are using reddit to push a wider narrative. 

If we identify superusers, are their posts seemingly neutral or do they tend to push a narrative?





###### Example: Embedding Altair & Hvplot Charts

This section will show examples of embedding interactive charts produced using [Altair](https://altair-viz.github.io) and [Hvplot](https://hvplot.pyviz.org/).

###### Altair Example

Below is a chart of the incidence of measles since 1928 for the 50 US states.



This was produced using Altair and embedded in this static web page. Note that you can also display Python code on this page:

```python
import altair as alt
alt.renderers.enable('notebook')
```

###### HvPlot Example

Lastly, the measles incidence produced using the HvPlot package:

<div id="hv-chart-1"></div>

###### Notes

- See the [lecture 13A slides](https://musa-550-fall-2021.github.io/slideslecture-13A.html) for the code that produced these plots.

**Important: When embedding charts, you will likely need to adjust the width/height of the charts before embedding them in the page so they fit nicely when embedded.**

###### Example: Embedding Folium charts

This post will show examples of embedding interactive maps produced using [Folium](https://github.com/python-visualization/folium).

###### OSMnx and Street Networks

The shortest route between the Art Museum and the Liberty Bell:

<div id="folium-chart-1"></div>

<br/>

###### Percentage of Households without Internet

The percentage of households without internet by county:

<div id="folium-chart-2"></div>

See the [lecture 9B slides](https://musa-550-fall-2021.github.io/slides/lecture-9B.html) and the [lecture 10A slides](https://musa-550-fall-2021.github.io/slides/lecture-10A.html) for the code that produced these plots.


## TL;DR
Reddit r/all posts, News API, parsing text, clustering and sentiment analysis, are there bad robots using reddit for bad stuff?

Logo paritally credited to Gan Khoon Lay from the Noun Project


[^1]: Digital 2021 April Global Statshot Report, [datareportal.com](https://datareportal.com/reports/digital-2021-april-global-statshot)
[^2]: Reddit Statistics, [oberlo.com](https://www.oberlo.com/blog/reddit-statistics)
[^3]: This is not the official name for the algorithm, but is what we’ll be calling it
[^4]: Meet The New Algorithm, Same As The Old Algorithm [thesocietypages.org](https://thesocietypages.org/cyborgology/2016/07/01/meet-the-new-algorithm-same-as-the-old-algorithm/)
[^5]: Seven-in-Ten Reddit Users Get News on the Site, [Pew Research Center](https://www.pewresearch.org/journalism/2016/02/25/reddit-news-users-more-likely-to-be-male-young-and-digital-in-their-news-preferences/)
