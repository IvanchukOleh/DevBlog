---
layout: post
title:  "Delegates, actions and events"
visible: 0
permalink: /delegates/
categories: [Unity]
tags: [c#, code, delegate, action, event]
author: Matanist
---

* content
{:toc}

## Вступ  
В цій статті спробую по простому розказати, що ж таке ті делегати, дії, події і як/коли їх варто використовувати в контексті розробки ігор на Unity.
Якщо дуже коротко, то:  
- delegate — це тип, який містить посилання на метод (методи) із визначеним списком параметрів та типом значення, що повертається. Використовуються, наприклад, для передачі методів, як параметрів, іншим методам;  
- action — по суті, заготовка делегата, але без значення, що повертається;  
- event — це елемент, який надає можливість класу (відправнику) надсилати сповіщення іншим класам (отримувачам, обробникам подій).  
  
## Delegates  
### Оголошення
Оголошення делегата є "заготовкою", що містить сигнатуру функції. Наприклад, делегат із одним параметром типу ```int```, що повертає значення типу ```string```:
```c#  
public delegate string MyDelegate(int patam);  
```  
Після створення "заготовки" потрібно створити екземпляр делегата:
```c#  
public MyDelegate Delegate1;
```  
Далі створеному делегату можна присвоювати значення методу, який відповідає вказаній сигнатурі:
```c#  
public string MyFunc(int param) {
    return param.ToString();
}

public void Start(){
    Delegate1 = MyFunc;
}
```  
Із C# 2.0 делегату можна присвоювати анонімні методи:  
```c#  
Delegate1 = delegate(int param) {
    return param.ToString();
};
```  
Із C# 3.0 також можна присвоювати лямбда-вирази:
```c#  
Delegate1 = value => value.ToString();
};
```  
## Actions  
  
## Events  
  
## Ключові відмінності  
  
## Корисні посилання:  
* [Delegates, Microsoft docs] (https://docs.microsoft.com/ru-ru/dotnet/csharp/programming-guide/delegates/ "Microsoft docs")  
* [Events, Microsoft docs] (https://docs.microsoft.com/ru-ru/dotnet/csharp/programming-guide/events/ "Microsoft docs")  