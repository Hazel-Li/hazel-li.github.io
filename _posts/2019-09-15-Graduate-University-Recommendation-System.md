---
title: "Overseas Graduate University Recommender System"
layout: post
date: 2019-09-15 20:18
image: /assets/images/beautifulsoup.jpg
tag: 
- data mining
- recommendation system
- text mining
headerImage: false
projects: true
hidden: true 
description: "This is a data mining project based on a forum called Gradcafe"
category: project
author: yitingli
externalLink: false
---
# Context

This is a Data Mining project based on a forum called <a href="https://www.thegradcafe.com/">Gradcafe</a>.

Prospective graduate students have long been wondering what factors are taken into consideration by the admission office and whether their academic achievements are sufficient for a particular program. Using a dataset with over 30,000 entries from TheGradCafe.com, this project aimed to provide insight on the admission requirements of each school and major, generate a recommendation list using Collaborative Filtering, and predict the admission rates for each school to assist students in their decision-making process.


## A shallow dive into our dataset

### Input

- **University Name**
- **Major** - Basically program name or major name in detail
- **Season**- Fall or Spring
- **Decision**  - Accepted, Rejected, Wait listed, Interview, or Other.
- **Decision Method** - Email, Website, Post, Phone or Other.
- **Decision Date**
- **Undergraduate GPA**
- **GRE Verbal** 
- **GRE Quant**
- **GRE Writing**
- **Status** - American, International, International with US degree or Other
- **Post date** 
- **Post Timestamp**
- **Comments**

### Data augmentation

1. Match every university with its world ranking
2. Classify majors into 10 fields

### Data Visualization

This gives us an overall picture of the distribution of the majors and the different admission rates of different majors.

![major.png](/assets/images/major.png)

This gives us an overall picture of the ditribution of the university of our dataset.

![uni.png](/assets/images/unicnt.png)

This gives us an overall picture of different GRE and GPA preferrence of each major.

![grade.png](/assets/images/grademajor.png)



## Information Retrieval from comments

We want to know whether the comments contain useful information for applicants to make desicions. 

![wordcloud.png](/assets/images/wordcloud.jpg)

Our goal is to genererate a word token list according to TF-IDF to display the keywords of every university. We are delighted to gain some valuable insights based on text analytics.Let's see what we got.

![tfidf.png](/assets/images/tfidf.jpg)

Both CMU and UCLA mention **sponsorship**，and some of the applicants feel excited about the results of **assitantships**. Applicants of UCB talks about their working experience in the field of industry. What's more, applicants of UCB lay emphasis on academic expreience such as experiments and papers.

## Website Preview

We designed a webpage with an interactive interface to display what we achieved.

Here we have login page.

![p1.png](/assets/images/p1.png)

Here we have information input page.

![p2.png](/assets/images/p2.png)

Here we have results.

![p3.png](/assets/images/p4.png)