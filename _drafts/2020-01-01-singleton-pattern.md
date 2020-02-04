---
layout: post
title:  "Singleton pattern in Unity"
categories: Unity
tags: unity c# pattern code
author: Matanist
---

* content
{:toc}

## Singleton

```c#
public class AutoCleanupSingleton<T> : MonoBehaviour where T : MonoBehaviour
{
    private static T _instance;
    public static T Instance
    {
        get
        {
            if (_instance == null)
            {
                _instance = FindObjectOfType<T>();
                if (_instance == null)
                {
                    GameObject obj = new GameObject("InstanceOf" + typeof(T));
                    _instance = obj.AddComponent<T>();
                }
            }
            return _instance;
        }
        private set => _instance = value;
    }

    protected virtual void Awake()
    {
        if (_instance != null)
        {
            Destroy(gameObject);
        }
        else
        {
            _instance = GetComponent<T>();
            DontDestroyOnLoad(gameObject);
        }
    }
}
```

