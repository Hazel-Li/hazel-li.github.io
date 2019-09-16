---
title: "Graduate University Recommendation System"
layout: post
date: 2019-09-15 20:18
image: /assets/images/beautifulsoup.jpg
tag: 
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
# Graduate University Recommendation System

This is a <span style="color:blue">data mining</span> project based on a forum called *Gradcafe*

Dedicated to: Zhengyao Zhu, Qinjin Yuan, Yiting Li

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

![major.png](/assests/images/major.png)

This gives us an overall picture of the ditribution of the university of our dataset.

![uni.png](/assests/images/unicnt.png)

This gives us an overall picture of different GRE and GPA preferrence of each major.

![grade.png](/assests/images/grademajor.png)



## Information Retrieval from comments

We want to know whether the comments contain useful information for applicants to make desicions. 

![wordcloud.png](/assests/images/worldcloud.png)

Our goal is to genererate a word token list according to TF-IDF to display the keywords of every university. We are delighted to gain some valuable insights based on text analytics.Let's see what we got.

![tfidf.png](/assests/images/tfidf.png)

Both CMU and UCLA mention **sponsorship**，and some of the applicants feel excited about the results of **assitantships**. Applicants of UCB talks about their working experience in the field of industry. What's more, applicants of UCB lay emphasis on academic expreience such as experiments and papers.