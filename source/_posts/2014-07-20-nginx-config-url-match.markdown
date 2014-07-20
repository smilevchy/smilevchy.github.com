---
layout: post
title: "nginx_config_url_match"
date: 2014-07-20 15:15:10 +0800
comments: true
categories: nginx
---

location smiley_019.png {
    root html/image;
}

location ~\.(gif|jpg|png)$ {
    root E:/Pictures;
}

In this condition, it will just match the latter, nor the former, which lacks a slash( must be added if it is not regex description)

---

<!-- more -->

after you add it:

location /smiley_019.png {
    root html/image;
}

location ~\.(gif|jpg|png)$ {
    root E:/Pictures;
}

In this condition, it will not match the former again because of nginx's matching rules about location. 
Here, the latter will override the former.

---

So, you need

1.Exact Match
location = /smiley_019.png {
    root html/image;
}

2.Override the match of latter regex match
location ^~ /smiley_019.png {
    root html/image;
}

Thus, the former match will not be overrided by the latter.