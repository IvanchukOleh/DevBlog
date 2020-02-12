---
layout: post
visible: 1
title:  "Post name"
categories: [Category]
tags: [tag]
author: Matanist
---

* content
{:toc}


## Object pooling

```c#
using System.Collections.Generic;
using UnityEngine;

public abstract class GenericObjectPool<T> : MonoBehaviour where T : Component
{
    [SerializeField] private T _prefab;
    public static GenericObjectPool<T> Instance { get; private set; }
    private Queue<T> _objects = new Queue<T>();

    private void Awake()
    {
        Instance = this;
    }

    public T Get()
    {
        if (_objects.Count == 0)
            AddObject();
        return _objects.Dequeue();
    }

    public void ReturnToPool(T objectToReturn)
    {
        objectToReturn.gameObject.SetActive(false);
        _objects.Enqueue(objectToReturn);
    }

    private void AddObject(int count = 1)
    {
        for (int i = 0; i < count; i++)
        {
            T obj = Instantiate(_prefab);
            obj.gameObject.SetActive(false);
            _objects.Enqueue(obj);
        }
    }
}
```