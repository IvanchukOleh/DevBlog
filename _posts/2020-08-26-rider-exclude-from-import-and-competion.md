---
layout: post
visible: 1
title:  "Excluding namespace/member/type from auto import settings"
categories: [Rider]
tags: [rider, code, tip]
author: Matanist
---

* content
{:toc}

В Rider можна налаштувати функцію автодоповнення.  
Зазвичай, коли виникає потреба часто використовувати класи List чи Vector3, за замовчуванням rider може 
пропонувати варіант автодоповнення із ```Boo.Lang``` або ```System.Numerics``` відповідно. 
```System.Collections.Generic``` чи ```UnityEngine``` може бути на другому місці в списку, через що треба натискати ```[↓]```, обираючи потрібний варіант.  
Оскільки ```Boo.Lang``` або ```System.Numerics``` зазвичай не використовуються, 
можна виключити їх зі списку пропонованих варіантів.  
Для цього треба в ```File/Settings/Editor/General/Auto Import``` додати рядки ```Boo.Lang.*``` та ```System.Numerics.*```  
відповідно.
  
  
  
  
  
Посилання:
[JetBrains](https://www.jetbrains.com/help/rider/Settings_Auto_Import.html "Документація JetBrains Rider")