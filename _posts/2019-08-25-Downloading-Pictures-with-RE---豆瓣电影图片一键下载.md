---
title: "Downloading Pictures with RE - 豆瓣电影图片一键下载"
layout: post
date: 2019-08-25 22:07
image: /assets/images/douban.jpg
headerImage: true
tag:
- Webspider
star: true
category: blog
author: yitingli
description: 爬虫第一步
---

和网页交互以及正则表达式需要用到的包，anaconda自带
```
import requests
import urllib.request
import re
```

### 1 Define a function to retrieve data from a webpage
这里写了个函数，主要是用来获取网页上的数据
```python
def get_html(url):
    ua_headers={'User-Agent':'Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10_6_8; en-us) AppleWebKit/534.50 (KHTML, like Gecko) Version/5.1 Safari/534.50'}
    request = urllib.request.Request(url,headers=ua_headers)
    html = requests.get(url, headers = ua_headers).text
    return html
```
### 2 Let's see what we get 

{% highlight raw %}
<img src="https://img1.doubanio.com/view/photo/sqxs/public/p457121168.jpg">
这里读取了该网页的内容，看看我们想要的图片是什么格式
{% endhighlight %}

```python
content=get_html('https://movie.douban.com/subject/1851857/all_photos')
print(content)
```

### 3 RE is a good tool to regulize and extract information
这里主要就是正则表达式读取形如src=“ #####  .jpg"的内容
然后把图片链接打印出来

```python
reg = r'src="(.+?\.jpg)"'
reg_img = re.compile(reg)#编译一下，运行更快
imglist=reg_img.findall(content)
for img in imglist:
    print(img)
```
[https://img1.doubanio.com/view/photo/sqxs/public/p2449147688.jpg](https://img1.doubanio.com/view/photo/sqxs/public/p2449147688.jpg)
[https://img3.doubanio.com/view/photo/sqxs/public/p1659302214.jpg](https://img3.doubanio.com/view/photo/sqxs/public/p1659302214.jpg)
[https://img3.doubanio.com/view/photo/sqxs/public/p902869130.jpg](https://img3.doubanio.com/view/photo/sqxs/public/p902869130.jpg)
[https://img3.doubanio.com/view/photo/sqxs/public/p1170817966.jpg](https://img3.doubanio.com/view/photo/sqxs/public/p1170817966.jpg)
[https://img3.doubanio.com/view/photo/sqxs/public/p902860861.jpg](https://img3.doubanio.com/view/photo/sqxs/public/p902860861.jpg)
[https://img3.doubanio.com/view/photo/sqxs/public/p902859926.jpg](https://img3.doubanio.com/view/photo/sqxs/public/p902859926.jpg)
[https://img3.doubanio.com/view/photo/sqxs/public/p1340704365.jpg](https://img3.doubanio.com/view/photo/sqxs/public/p1340704365.jpg)

差不多就会告诉我们这样子

### 4 Here we go :
```python
x = 0
for img in imglist:
    urllib.request.urlretrieve(img, '%s.jpg' %x)
    x += 1
```
函数：urllib.urlretrieve(url[, filename[, reporthook[, data]]])   
这里就是给了个filename用数字序列命名

好了成功运行之后就会发现
![image.png](/assets/images/douban_pic.png)
<figcaption class="caption">Downloading pictures</figcaption>


整个下载过程非常快，因为是缩略图-，-
但是我之前试了imdb的图片页面，就是高清大图，一个世纪下不了一张，
Gary Oldman的脸下到一半就卡住了

灵感来自于：[cnblogs](https://www.cnblogs.com/Axi8/p/5757270.html)
