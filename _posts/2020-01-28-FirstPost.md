---
layout: post
title:  "First post"
categories: Unity
tags: unity, c#
author: Matanist
---

* content
{:toc}

Пробна публікація із куском коду

```c#
private void Awake()
{
    if (_instance == null)
    {
        _instance = this;
        DontDestroyOnLoad(gameObject);
    }
    else if (_instance != this)
    {
        Destroy(gameObject);
    }
}
```
