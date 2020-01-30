---
layout: post
title:  "Coroutine() vs \"Coroutine\" vs nameof(Coroutine)"
categories: Unity
tags: unity code сoroutine c#
author: Matanist
---

* content
{:toc}

## Corutines

Детальніше про те, що то таке і з чим його їдять можна почитати тут: 
[Official Unity manual](https://docs.unity3d.com/Manual/Coroutines.html)

Тут детальніше розгляну різні способи їх виклику.  
Зробити це можна такими трьома способами:
```c#
StartCoroutine(ExampleCoroutine());
StartCoroutine(nameof(ExampleCoroutine));
StartCoroutine("ExampleCoroutine");
```

Розглянемо відмінності між ними. 





Другий і третій варіант є тотожними, але другий простіший під час налагодження та тестування, тому краще використовувати його.  

Для тестування написав клас і прикріпив його до порожнього об’єкта на сцені:
```c#
public class ExampleScript : MonoBehaviour
{
    private int count = 0;

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.A))
            StartCoroutine(nameof(ExampleCoroutine));

        if (Input.GetKeyDown(KeyCode.C))
            StopCoroutine(nameof(ExampleCoroutine));
    }

    IEnumerator ExampleCoroutine()
    {
        int i = count++;
        Debug.Log("ExampleScript::ExampleCoroutine>> Coroutine " + i + " start");
        yield return new WaitForSeconds(2f);
        Debug.Log("ExampleScript::ExampleCoroutine>> Coroutine " + i + " end");
    }
}
```

При натисканні на A викликається ExampleCoroutine. При натисканні на C зупиняється.  
Якщо використовувати 2 і 3 варіанти звернення і різні їх комбінації, то при натисканні на A починає виконуватись ExampleCoroutine.
При повторному натисканні паралельно починає виконуватись новий екземпляр ExampleCoroutine. При натисканні на C припиняють виконуватися всі екземпляри ExampleCoroutine, що виконуються в цей момент.
Якщо використовувати перший варіант, то при натисканні на C нічого не відбувається і виконання ExampleCoroutine не припиняється.







































