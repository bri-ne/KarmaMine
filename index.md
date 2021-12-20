---
layout: default
altair-loader:
  altair-chart-1: "charts/measlesAltair.json"
hv-loader:
  hv-chart-1: ["charts/measlesHvplot.html", "500"] # second argument is the desired height
folium-loader:
  folium-chart-1: ["charts/foliumChart.html", "400"] # second argument is the desired height
  folium-chart-2: ["charts/percent_no_internet.html", "400"] # second argument is the desired height
---

# A Look at Reddit's Values, IRL Events, and Possible Bad Actors
*Gianluca Mangiapane, Bri Cervantes*


**[TL;DR](#tldr)**

## Our Motivation

Reddit is known as the front page of the internet, but what does it take to get on the front page of the internet’s front page? 

As the 15th most used social media network in the world[^1], Reddit boasted more than 430 monthly active users in 2019.[^2] Unlike Facebook or Instagram, Reddit is structured as a forum based platform hosting 2.8 million sub-forums, known as subreddits, where users can discuss anything from [Python](https://www.reddit.com/r/Python/), to  [Wall Street](https://www.reddit.com/r/wallstreetbets/), to things that make them say [‘aww’](https://www.reddit.com/r/aww/). Once subscribed to a subreddit, user’s can post content relating to the subreddit, ask questions, and engage in discussions with other reddit users. In 2019 alone, there were roughly 199 million posts, 1.7 million comments, and 32 billion upvotes made by Reddit users. This is all to say there’s a lot of competition for the front page of Reddit but if you make it there, you’re guaranteed to capture a lot of engagement.


### The Front Page 

The front page of Reddit is not explicitly defined, but most users consider it to be the pseudo subreddit r/all. R/all is a ‘default’ subreddit, meaning each new user is automatically subscribed to it when they first create their account. And unlike other true subreddits, users can’t post directly to r/all, instead very popular posts from other subreddits are published there by Reddit’s r/all algorithm.[^3] Generally, Reddit’s r/all algorithm uses a combination of how recently a post was made, “how many upvotes it has received, and how recently it’s been upvoted” to determine front-page worthy posts.[^4] 

But if you don’t want to leave it up to chance, how can you make sure you make it to the front-page? We know that popular posts make it to the front-page, but is there a pattern to what makes a post popular? Using PRAW, a Reddit API wrapper, we will investigate what r/all posts have in common and explore which subreddits (super-subreddits) and users (superusers) make it to the front page the most. Additionally, we’ll incorporate data from the AP API to investigate whether the popularity of r/all posts is  influenced by world events.

### Question We Set Out to Answer, and the Ones We Actually Did

#### 1. What does Reddit Value? What are the common characteristics/patterns in top r/all posts?

As the front page of the internet, Reddit definitely has its own defined culture, shaped by its users. Like-minded individuals share news, memes, and references on their subscribed subreddits. While sometimes these would make no sense outside of Reddit, within Reddit it’s all relevant day to day interactions. If a post in a subreddit gains enough traffic amongst its users through upvotes and comments, Reddit’s algorithm identifies it as a popular post that can be pushed to the r/all frontpage. The posts in r/all are the most upvoted and seen posts on reddit, drawing the heaviest traffic of users. Regardless of the subreddit the initial post is made in, subscribers across the entire Reddit site are exposed to the post once it starts trending on the front page. We want to look at the top posts of all time, to identify what are the popular cultural phenomena and topics of discussion that Reddit values. Are there identifiable common characteristics that help us better understand why these posts were so successful? Are there subreddits that appear more frequently in the top posts that we can label as super subreddits driving their message? Looking further, are there frequent usernames (subscribers) that appear in the top posts as well that we can label as superusers, and do their posts have common or diverse themes. We will aim to use scikit-learn cluster analysis to identify groups of similar posts, along with running a sentiment analysis on the posts beforehand to include emotion as an additional feature for the pattern analysis. 


#### 2. How representative is Reddit’s front page of what’s happening in the world? 

While Reddit is a subculture unto itself ([ex.1](https://www.reddit.com/r/Music/comments/56cdgm/ama_im_really_rick_astley_i_swear_and_to/), [ex.2](http://i0.kym-cdn.com/entries/icons/original/000/016/212/manning.png)), it’s not possible for the platform to fully extricate itself from the rest of the IRL world. As a result, its lively subculture not only amplifies reddit-wide values, but it can also act as an accelerant for ideas and narratives that have context outside of Reddit. Further, the loyalty that users have to the site, might mean they use it for more than just fun. In 2016, the Pew Research Center found that 78% of Reddit users get their news from the site.[^5] We’ll investigate the connections that recent r/all posts have with news headlines by identifying if they share common themes. Additionally, we’ll compare sentiment analysis results from posts and news headlines to investigate if general feelings are shared across platforms.

#### 3. How does Reddit impact the real world? AKA why does understanding Reddit matter?

It’s clear the IRL world can influence what people talk about on Reddit, but can small actors use Reddit to steer larger narratives? Last year’s rise of r/WallStreetsBets (WSB) exposed the nation to the reality-creating power of Reddit. We all watched, or maybe even participated, as the subculture of WSB spilled out over the stock market, turning internet ideas into IRL impacts. But given that Reddit is open to anyone and typically promotes user anonymity, anyone can harness the platform’s culture-shifting power with the right resources. In addition to our cluster analysis of both r/all posts and news headlines, we hope to identify features that may be associated with documented qualities of robot users. Similarly, we’ll investigate posts and comments for signs of (bad) robot activity. Further, if our analysis in the previous steps identifies superusers and super subreddits, we’ll explore the common themes of their posts and users activity to draw some conclusions about whether they are using reddit to push a wider narrative. 

If we identify superusers, are their posts seemingly neutral or do they tend to push a narrative?





###### Example: Embedding Altair & Hvplot Charts

This section will show examples of embedding interactive charts produced using [Altair](https://altair-viz.github.io) and [Hvplot](https://hvplot.pyviz.org/).

###### Altair Example

Below is a chart of the incidence of measles since 1928 for the 50 US states.

<div id="altair-chart-1"></div>

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
