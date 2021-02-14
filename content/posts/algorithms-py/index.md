---
title: "Algorithms with Python"
date: 2021-02-14T14:35:55+09:00
draft: false

summary: "A note on writing algorithms in python"

resources:
- name: "featured-image"
  src: "luah-jun-yang-iqOz97xU9xg-unsplash.jpg"
- name: "featured-image-preview"
  src: "luah-jun-yang-iqOz97xU9xg-unsplash.jpg"

tags: ["code", "py"]
categories: ["Memo"]

lightgallery: true
---

<br>

## Intro :snake:
- I always forget how to do it, so I'll write it down here.

<br>

## list -> int

```python
lst = [1, 2, 3]

int(''.join(map(str, lst)))

>>> 123
```
