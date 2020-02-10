---
layout: post
title:  "ScriptTemplates in Unity3D"
visible: 1
categories: Unity
tags: [unity, tip, code, editor, region, template]
author: Matanist
---

* content
{:toc}

## ScriptTemplates
При створенні скрипта через редактор Unity отримується файл із таким вмістом:
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ExampleScript : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```
З часом набридає кожен раз видаляти коментарі типу ```Start is called before the first frame update``` та й далеко не в кожному скрипті потрібні методи Update() та Start().  
Вміст скрипта за замовчуванням можна змінити.





Для цього потрібно перейти в папку, де встановлена поточна версія Unity, далі ```Editor -> Data -> Resources -> ScriptTemplates```.  
Приклад шляху до Unity 2019.3.0f6, встановленої через UnityHub:  
```C:\Program Files\Unity\Hub\Editor\2019.3.0f6\Editor\Data\Resources\ScriptTemplates```  
В цій папці буде файл ```81-C# Script-NewBehaviourScript.cs.txt```.  
Вміст за замовчуванням:
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class #SCRIPTNAME# : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        #NOTRIM#
    }

    // Update is called once per frame
    void Update()
    {
        #NOTRIM#
    }
}
```
Я зазвичай змінюю його таким чином:
```c#
using UnityEngine;

public class #SCRIPTNAME# : MonoBehaviour
{
    #region Variables
    #NOTRIM#
    #endregion

    #region UnityMethods
    private void Start()
    {
        #NOTRIM#
    }
    #endregion
}
```
Одразу додаю ```#region```, оскільки це значно спрощує навігацію по файлу. Завжди змінні і Unity-методи виділяю в окремі блоки.





