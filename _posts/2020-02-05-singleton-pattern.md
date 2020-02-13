---
layout: post
title:  "Singleton pattern in Unity3D"
visible: 1
categories: [Unity]
tags: [unity, c#, pattern, singleton]
author: Matanist
---

* content
{:toc}

## Singleton
Патерн проектування, який гарантує, що буде створено лише один екземпляр певного класу, а також забезпечує точку доступу до нього.





Принциповою відмінністю від глобальних змінних є те, що об’єкт буде створено лише за необхідності.

## Реалізація
Найоптимальнішою і найзручнішою у використанні для мене є реалізація за допомогою [generic-класу](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/generic-classes "Microsoft docs"):
  
```c#
using UnityEngine;

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
    }

    protected virtual void Awake()
    {
        if (_instance != null)
        {
            //видалення дублікатів об’єкта
            Destroy(gameObject);
        }
        else
        {
            //якщо екземпляр класу міститься на сцені до першого звернення через Instance, то він зберігається як єдиний
            _instance = GetComponent<T>();
            //об’єкт не видаляється при переході від одної сцени до іншої
            DontDestroyOnLoad(gameObject);
        }
    }
}
```
  
Використання generic-класу дозволяє уникнути багаторазового дублювання однакового коду в кожному класі, який має бути сінглтоном. Достатньо вказати, що клас буде наслідуватись від ```AutoCleanupSingleton<T>()```, де ```T``` — ім’я класу:
  
```c#
public class SingletonClassExample : AutoCleanupSingleton<SingletonClassExample>
{
    public int ExampleInt;
    //...
    protected override void Awake()
    {
        base.Awake();
        ExampleInt = 5;
    }
    //...
}
```
  
За потреби можна вже в конкретному класі переозначити метод ```Awake()```. Використання ```virtual``` вбереже від випадкового переозначення методу ```Awake()``` і можливих помилок, пов’язаних із цим.
Після оголошення класу таким чином доступ до змінної ```ExampleInt``` буде із будь-якого місця в коді:
  
```c#
SingletonClassExample.Instance.ExampleIntField
```
  
## Використання
Використання цього патерна доречне при створенні різних ігрових менеджерів.  

## Корисні посилання
- [YouTube, Jason Weimann, особливості використання Singleton в Unity \(англ\)](https://youtu.be/ptkxRn0HCJc "Канал із туторіалами по Unity (англ)")
- [metanit.com, стаття про Singleton \(рос\)](https://metanit.com/sharp/patterns/2.3.php "Цікавий сайт із купою матеріалів по програмуванню (рос)")  