---
title: " Best ever Netdisk is ------ Github!"
layout: post
date: 2019-09-29 22:44
image: /assets/images/beautifulsoup.jpg
headerImage: false
tag:
- Trick
star: true
category: blog
author: yitingli
description: 
---

## Preface

Have you ever troubled by having things uploaded and downloaded? There are many methods for you to transfer your files without USB. We have Baidu Netdisk, iCloud, Onedrive, etc. But some of them charge you extra money and others can not give you a prompt experience.

[GitHub](https://github.com/) is an American company that provides hosting for software development version control using Git. What's more, it can be serve as a free **repository**.

## Here is the instruction!

### The environment you need
1. VS Code
2. Github Desktop or your terminal

###Steps
1. If you don't have an account, then create a new github account

2. Add a new repository

   ![image-20190929225500159](/Users/liyiting/hazel-li.github.io/assets/images/r1.png)

3. Open your Visual Studio Code

   ![image-20190929225814960](/Users/liyiting/hazel-li.github.io/assets/images/r2.png)

   Run the following Code:

   ```git
   git init
   git add README.md
   git commit -m "first commit"
   git remote add origin https://github.com/********.git
   git push -u origin master
   ```
   
   Every time you want to update your files:
   
   ```git
   git commit -m "first commit"
   git remote add origin https://github.com/********.git
   git push -u origin master
   ```
   
4. Github Desktop can trace every changed your made

   ![image-20190929231136525](/Users/liyiting/hazel-li.github.io/assets/images/r3.png)

To sum up, it is a quick way to have your files stored online. It works well with codes and documents. But you have a big digest for videos, it should not be your choice.