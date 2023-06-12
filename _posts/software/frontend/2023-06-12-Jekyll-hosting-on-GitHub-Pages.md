---
title: Jekyll hosting on GitHub Pages
layout: post
date: 2023-06-12 01:00 -800
categories: [software, frontend]
tags: [jekyll]
---
Make sure to make the GitHub repository and "url" field in your _config.yml file in Jekyll matches your username exactly. I had forgotten to match the username exactly and spent much of my time wondering why my url/baseurl entries weren't working. And now I know.

```
# Given my GitHub username "Jonathan-Lam"
url: https://jonathan-lam.github.io
```
