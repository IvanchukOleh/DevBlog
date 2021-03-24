---
layout: post
title:  "Namespace management in JetBrains Rider"
visible: 1
categories: Unity
tags: [unity, tip, code, rider, jetbrains]
author: Matanist
---

* content
{:toc}

## Проблема
Треба прибрати певні папки з автоматичної генерації простору імен.  
Нащо взагалі використовувати простори імен писати не буду. Це штука однозначно потрібна і просто "must have" в кожному проекті. Rider вміє автоматично генерувати простір імен відповідно до розміщення файлу. При цьому ```Assets\Scripts``` чудово розпізнається і Rider ці папки (якщо саме в такій послідовності) ігнорує.  
Можна навіть вказати ```RootNamespace``` до проекту, який автоматично додасться на початок. Більше того, для кожного AssemblyDefinition можна задати власний ```RootNamespace```.  
Танці з бубном починаються, коли ієрархія в проекті має бути складніша і деякі папки в простір імен включати не треба.





## Сценарій використання
При розробці окремого модуля, який буде розповсюджуватись пакетом через GitHub, Unity [рекомендує](https://docs.unity3d.com/Manual/cus-layout.html "Unity docs") таку структуру проекту:
```
<root>
  ...
  ├── Editor
  │   ├── Unity.[YourPackageName].Editor.asmdef
  │   └── EditorExample.cs
  ├── Runtime
  │   ├── Unity.[YourPackageName].asmdef
  │   └── RuntimeExample.cs
  ├── Tests
  │   ├── Editor
  │   │   ├── Unity.[YourPackageName].Editor.Tests.asmdef
  │   │   └── EditorExampleTest.cs
  │   └── Runtime
  │        ├── Unity.[YourPackageName].Tests.asmdef
  │        └── RuntimeExampleTest.cs
  ...
```
Саме така ієрархія дійсно має сенс, але, в той же час, нема необхідності робити простір імен ```<НазваМодуля>\Runtime\Scripts```. Значно зручніше, щоб простір імен був ```<Розробник>.<НазваМодуля>```, але кожен раз вручну виправляти його на потрібний, а потім ще дивитись на повідомлення ```Namespace does not corespond to file location``` — ще те задоволення...

## Рішення
Зайти в налаштування Rider і прибрати зайві галочки з тих папок, які мають ігноруватись.  
  
Зробити це можна так:  
- відкрити проект в Rider;  
- відкрити вікно **Explorer** (мишкою на панелі зліва, або ж ```Alt+1```);  
- впевнитись, що вгорі вікна вибрано варіант **Solution** (за замовчуванням зазвичай "Unity");  
- клікнути **ПКМ** на папці, яку треба прибрати;  
- вибрати **Properties** (або ```AltEnter```);  
- прибрати галочку **Editable->Namespace provider**;  
- потішитись отриманому результату;  
