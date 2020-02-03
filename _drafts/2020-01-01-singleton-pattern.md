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
                Debug.Log("AutoCleanupSingleton::Instance>> Instance of " + nameof(T) + " is null. " +
                          "Try to found it on the scene"); 
                _instance = GameObject.FindObjectOfType<T>();
                if (_instance == null)
                {
                    Debug.Log("AutoCleanupSingleton::Instance>> Created new Instance of " + nameof(T));
                    GameObject obj = new GameObject("Instance of " + nameof(T));
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
            Destroy(this);
        

    }
}
```

