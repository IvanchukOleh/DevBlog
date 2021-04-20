---
layout: post
visible: 1
title:  "Attributes in Unity3D"
categories: [Unity]
tags: [attribute, tip]
author: Matanist
---

* content
{:toc}

## Атрибути:  
* ```[InitializeOnLoad]```  
* ```[RuntimeInitializeOnLoadMethod]```  
* ```[InspectorName]```  
* ```[MenuItem("...")]```  





## InitializeOnLoad  
Атрибут ```[InitializeOnLoad]``` корисний в тих випадках, коли потрібно запустити якийсь скрипт одразу після запуску редактора Unity.  
Для прикладу, це може бути перевірка наявності якогось файлу налаштувань в папці Resources. Якщо файл відсутній, то можна створити якийсь за замовчуванням або вивести повідомлення про помилку.  
  
Використання:  
Атрибут застосовується до класу. Оскільки це фішка, пов’язана із редактором Unity, то файл обов’язково має бути розміщений в папці Editor і, відповідно, буде доступний лише в редакторі.  
Код, який має виконатися, треба помістити в статичний конструктор класу.  
Таким чином, кожен раз при відкритті редактора або перекомпілюванні скриптів, буде викликатися потрібний метод.  
```c#
using UnityEditor;

[InitializeOnLoad]
public class ExampleScript
{
    static ExampleScript()
    {
        //перевірка наявності файлів, тощо
    }
}
```  
  
## RuntimeInitializeOnLoadMethod  
Атрибут ```[RuntimeInitializeOnLoadMethod]``` корисний в тих випадках, коли потрібно мати можливість запускати гру з будь-якої сцени, а не лише зі сцени з пре-лоадером, чи головним меню.  
Для прикладу, коли потрібно в першу чергу переконатися, що налаштування гри завантажено, на сцені обов’язково є якийсь ManagerScript або ж коли потрібно задати чіткий порядок створення різних менеджерів.  
  
Використання:  
Атрибут застосовується до конкретного статичного методу в **не** MonoBehaviour скрипті.  
Використовуючи параметри можна вказати, коли саме має викликатися метод:  
* AfterSceneLoad - після завантаження першої довільної сцени;  
* BeforeSceneLoad - перед завантаженням першої довільної сцени;  
* AfterAssembliesLoaded - when all assemblies are loaded and preloaded assets are initialized;  
* BeforeSplashScreen - перед показом SplashScreen;  
* SubsystemRegistration - callback для реєстрації підсистем.  
  
Приклад:  
```c#
using UnityEngine;

public class ExampleScript
{
    [RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.BeforeSceneLoad)]
    public static void ExampleMethod1()
    {
        Debug.Log("ExampleScript::ExampleMethod>> BeforeSceneLoad");
    }
    
    [RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.AfterSceneLoad)]
    public static void ExampleMethod2()
    {
        Debug.Log("ExampleScript::ExampleMethod>> AfterSceneLoad");
    }
}
```
**Важливо:** при оголошенні декількох методів із однаковими параметрами порядок їх виклику відповідно до порядку в коді не гарантується.

## InspectorName  
Атрибут ```[InspectorName("<name>")]``` використовується, коли треба змінити назву елемента enum в інспекторі Unity.  

Приклад:  
```c#  
public enum ModelImporterIndexFormat  
{  
    Auto = 0,  
    [InspectorName("16 bits")]  
    UInt16 = 1,  
    [InspectorName("32 bits")]  
    UInt32 = 2,  
}  
```  
## MenuItem
Атрибут ```[MenuItem("<name>")]``` дозволяє додати ```статичний``` метод до випадаючого меню редактора. Через ```/``` задається шлях (ієрархія) пункту меню.  
```c#
[MenuItem("MyMenu/Do Something")]
static void DoSomething()
{
    Debug.Log("Doing Something...");
}
```
Додатково можна задати для методу відповідну клавішу/комбінацію клавіш. 
Для цього в кінці назви методу треба додати символ 
```%```(ctrl on Windows, cmd on macOS), 
```#```(shift) або 
```&```(alt) і додати позначення клавіші. 
Якщо потрібно задати клавішу без ```ctrl```, ```shift``` чи ```alt```, 
перед позначенням клавіші треба додати символ ```_```.  
Можна додавати клавіші не лише з буквами, а й деякі спеціальні:  
```LEFT```, ```RIGHT```, ```UP```, ```DOWN```, ```F1``` .. ```F12```, ```HOME```, ```END```, ```PGUP```, ```PGDN```.  
Приклади:
- ...```"MyMenu/DoSomething %d"``` - комбінація Ctrl+D;
- ...```"MyMenu/DoSomething _d"``` - лише клавіша D;
- ...```"MyMenu/DoSomething #LEFT"``` - комбінація Shift+Left;

## Корисні посилання:  
* [Running Editor Script Code on Launch, Unity docs](https://docs.unity3d.com/Manual/RunningEditorCodeOnLaunch.html "Документація Unity")  
* [RuntimeInitializeOnLoadMethodAttribute, Unity docs](https://low-scope.com/unity-tips-1-dont-use-your-first-scene-for-global-script-initialization "Документація Unity")  
* [InspectorNameAttribute, Unity docs](https://docs.unity3d.com/ScriptReference/InspectorNameAttribute.html "Документація Unity")  
* [Unity Tip: Don’t use your first scene for global Script initialization, Low scope blog](https://docs.unity3d.com/ScriptReference/RuntimeInitializeOnLoadMethodAttribute.html "Стаття, з якої взяв детальнішу інформацію")  
* [UnityEditor.MenuItem, UnityDocs](https://docs.unity3d.com/ScriptReference/MenuItem.html)  
