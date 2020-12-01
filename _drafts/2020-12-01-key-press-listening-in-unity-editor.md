---
layout: post
visible: 0
title:  "Post name"
categories: [Category]
tags: [tag]
author: Matanist
---

* content
{:toc}


При розробці власних редакторів до Unity виникає потреба відслідковування натискання клавіш.  
Оскільки в скрипті редактора відсутній метод Update в звичному розумінні, треба шукати інші способи.  
Один із варіантів — помістити в метод 
```c#
private void OnSceleGUI() {
    Event e = Event.current;
    if (e.type == EventType.KeyDown && e.control && e.keyCode == KeyCode.S)
        DoSomething();
}
```
https://answers.unity.com/questions/381630/listen-for-a-key-in-edit-mode.html


# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6

*italic*
_italic_
**bold**
__bold__
***bold italic***
___bold italic___

>Виділений абзац
>>Виділений підпункт абзацу

- перший пункт маркованого списку
- другий пункт маркованого списку

1. перший пункт нумерованого списку
8. другий пункт нумерованого списку
3. третій пункт нумерованого списку
	2. перший підпункт нумерованого списку
	2. другий підпункт нумерованого списку
2. четвертий пункт нумерованого списку

```c#
код
```

Горизонтальні лінії:
***
---
_________________


Посилання:
[Duck Duck Go](https://duckduckgo.com)
[Duck Duck Go](https://duckduckgo.com "The best search engine for privacy")
<https://www.markdownguide.org>
[![назва](/assets/image.png "напис при наведенні мишкою")](посилання, куди перейде користувач після кліку по картинці)
![назва, яку буде видно](/assets/image.png)

