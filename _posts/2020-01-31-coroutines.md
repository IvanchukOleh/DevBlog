---
layout: post
title:  "Coroutine() vs \"Coroutine\" vs nameof(Coroutine)"
categories: Unity
tags: unity сoroutine code c#
author: Matanist
---

* content
{:toc}

## Corutines

Детальніше про те, що то таке і з чим його їдять можна почитати тут: [official Unity manual](https://docs.unity3d.com/Manual/Coroutines.html)

Я ж детальніше розгляну різні способи їх виклику.  
Зробити це можна такими трьома способами:
```c#
StartCoroutine(nameof(ExampleCoroutine));
StartCoroutine("ExampleCoroutine");
StartCoroutine(ExampleCoroutine());
```

Розглянемо відмінності між ними. 





Для тестування я написав скрипт і прикріпив його до порожнього об’єкта на сцені:
```c#
public class ExampleScript : MonoBehaviour
{
    private Coroutine myCoroutine1;
    private Coroutine myCoroutine2;
    private Coroutine myCoroutine3;
    private int count = 1;

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            StartCoroutine(nameof(ExampleCoroutine));
            StartCoroutine("ExampleCoroutine");
            StartCoroutine(ExampleCoroutine());
            myCoroutine1 = StartCoroutine(nameof(ExampleCoroutine));
            myCoroutine2 = StartCoroutine("ExampleCoroutine");
            myCoroutine3 = StartCoroutine(ExampleCoroutine());
        }
        if (Input.GetKeyDown(KeyCode.Alpha1))
            StopCoroutine(nameof(ExampleCoroutine));
        if (Input.GetKeyDown(KeyCode.Alpha2))
            StopCoroutine("ExampleCoroutine");
        if (Input.GetKeyDown(KeyCode.Alpha3))
            StopCoroutine(ExampleCoroutine());
        if (Input.GetKeyDown(KeyCode.Alpha4))
            StopCoroutine(myCoroutine1);
        if (Input.GetKeyDown(KeyCode.Alpha5))
            StopCoroutine(myCoroutine2);
        if (Input.GetKeyDown(KeyCode.Alpha6))
            StopCoroutine(myCoroutine3);
    }

    IEnumerator ExampleCoroutine()
    {
        int i = count++;
        Debug.Log("ExampleScript::ExampleCoroutine>> Coroutine " + i + " start");
        yield return new WaitForSeconds(3f);
        Debug.Log("ExampleScript::ExampleCoroutine>> Coroutine " + i + " end");
    }
}
```
При натисканні на пробіл викликається ExampleCoroutine різними способами. При натисканні на клавіші від 1 до 6 припиняється виконання ExampleCoroutine різними способами.  

## Результати:
- При виклику ```StopCoroutine(nameof(ExampleCoroutine));``` та ```StopCoroutine("ExampleCoroutine");``` припиняють виконання 1, 2, 4 і 5 екземпляри. 3 і 6 продовжують виконуватися.  
- При виклику ```StopCoroutine(ExampleCoroutine());``` нічого не відбувається. Всі екземпляри продовжують виконання.  
- При виклику ```StopCoroutine(myCoroutine1);```, ```StopCoroutine(myCoroutine2);```, ```StopCoroutine(myCoroutine3);``` припиняють виконання лише ```myCoroutine1```, ```myCoroutine2``` та ```myCoroutine3``` відповідно.  

## Підсумок
- Звертання ```nameof(ExampleCoroutine)``` та ```"ExampleCoroutine"``` є тотожними, але краще використовувати перший варіант, бо це значно спрощує процес налагодження.  
- ```ExampleCoroutine()``` є сенс використовувати, коли потрібна гарантія, що виконання методу не припиниться випадково викликом ```StopCoroutine(nameof(ExampleCoroutine));``` в іншому місці.