---
layout: post
title:  "Live templates in JetBrains Rider"
visible: 1
categories: [Rider]
tags: [rider, code, tip]
author: Matanist
---

* content
{:toc}

Корисна штука в JetBrains Rider: Live templates

Дозволяє створювати власні скорочення, або редагувати вже наявні.  
Для прикладу, можна змінити скорочення ```log```, щоб в консоль виводилась одразу інформація про клас і метод, із якого виводиться повідомлення, або додати скорочення для виведення повідомлень певним кольором.  

Якщо в коді написати ```log```, то покажеться список можливих варіантів для автозаміни:  

![Settings](/assets/2020-01-30-rider-live-templates-3.png)  

Якщо обрати ```log```, то вставиться
```c#
Debug.Log("ExampleScript::ExampleMethod>> ");
```





Налаштування скорочень для C# можна знайти тут:  
Settings -> Editor -> LiveTemplates -> C#  

![Settings](/assets/2020-01-30-rider-live-templates-1.png)  

Змінні виділяються знаком $ з двох боків. $END$ — зарезервоване ім’я, яким позначається місце, куди переведеться курсор. 
Решті можна присвоїти власне значення (Edit variables). 
Змінити/присвоїти значення можна, натиснувши Change macro. 
Якщо залишити галочку "Editable", то курсор переведеться на місце змінної, навіть якщо в означенні скорочення є $END$.  

![Variables editing](/assets/2020-01-30-rider-live-templates-2.png)  

## Ключові слова
```$SELECTION$``` — те, що було виділено на час набирання скорочення  
```$END$``` — точка, куди переведеться вказівник після введення всіх змінних, помічених як "Editable"  

## Часто використовувані скорочення
**log**  
```c#
UnityEngine.Debug.Log("$CLASS$::$MEMBER$>> $SELECTION$$END$");
```
```$CLASS$``` — containing type name  
```$MEMBER$``` — containing type member name  
  
**logyellow**  
```c#
UnityEngine.Debug.Log("<color=yellow>$CLASS$::$MEMBER$>></color> $SELECTION$$END$");
```
```$CLASS$``` — containing type name  
```$MEMBER$``` — containing type member name  
  
**todo**
```c#
//TODO: [$DATE$] $SELECTION$$END$
```
```$DATE$``` — current date and time in specified format [yyyy.MM.dd HH:mm]  

**note**
```c#
//NOTE: [$DATE$] $SELECTION$$END$
```
```$DATE$``` — current date and time in specified format [yyyy.MM.dd HH:mm]  
