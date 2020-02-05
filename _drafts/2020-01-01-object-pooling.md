---
layout: post
title:  "Post name"
categories: Category
tags: tag
author: Matanist
---

* content
{:toc}

## Object pooling

generic pool:
- public T Get();
- public void ReturnToPool(T objectToReturn);
- private void AddObject(int count = 1);