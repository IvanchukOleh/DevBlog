---
layout: post
visible: 1
title:  "Extension methods"
categories: [Unity]
tags: [c#, tip]
author: Matanist
---

* content
{:toc}

## Суть проблеми:  
В Unity3D класи ```Vector2``` і ```Vector3``` не серіалізуються. Через це виникає необхідність створювати власні класи типу ```SerializableVector3``` (я зазвичай використовую назву ```SVector3```) з атрибутом ```[Serializable]```.  
Є декілька способів переведення одного в інше.  





## Різні підходи  
Розглянемо різні способи переведення ```SVector3``` у ```Vector3``` і навпаки:  
1. Створити в класі ```SVector3``` статичні типу ```public static SVector3 From(Vector3 vector3)``` і ```public static Vector3 To(SVector3 vector3)```.  
В такому разі доведеться багато разів писати в коді довгий вираз із параметром:  
```c#
SVector3 serializableVector = SVector3.To(myVector3)
```
Мені це здається не дуже зручним, тому в якийсь момент від такого підходу відмовився.  
2. Створити конструктор із відповідним параметром ```public SVector3(Vector3 vector3)``` та метод ```public Vector3 ToVector3()```;  
За такого підходу при переведенні ```SVector3``` у ```Vector3``` достатньо написати  
```c#
Vector3 vector3 = mySVector3.ToVector3();
```
але при переведенні до ```SVector3``` потрібно кожен раз писати  
```c#
SVector3 serializableVector = new SVector3(myVector3);
```
що додає певних незручностей, бо знову потрібно вказувати додатково параметр.  
3. Використати 2 варіант в комбінації із методами розширення для Vector3  
Для переведення ```Vector3``` у ```SVector3``` можна створити статичний клас із методами розширення ```Vector3```:  
```c#
public static class Vector3Extension
{
    public static SVector3 ToSVector3(this Vector3 vector3)
    {
        return new SVector3(vector3);
    }
}
```
Тепер можна буде, наприклад, написати ```transform.position.ToSVector3()``` і отримати серіалізовану позицію об’єкта.  

## Корисні посилання:  
* [Extension Methods (C# Programming Guide)](https://docs.microsoft.com/uk-ua/dotnet/csharp/programming-guide/classes-and-structs/extension-methods "Документація Microsoft")