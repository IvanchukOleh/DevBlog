---
layout: post
visible: 1
title:  "Rotation як в інспекторі Transform"
categories: [Unity]
tags: [editor, tip, rotation, inspector]
author: Matanist
---

* content
{:toc}

## Суть проблеми
При показі поточного повороту об’єкта в ```Custom Editor``` часто можна бачити, що в інспекторі Unity в ```Transform``` показується геть інше значення, ніж ```rotation.eulerAngles``` чи ```localRotation.eulerAngles``` у власному редакторі.

##Рішення
```c#
UnityEditor.TransformUtils
public static Vector3 GetInspectorRotation(Transform t);
public static void SetInspectorRotation(Transform t, Vector3 r);
```





Посилання:
[UnityDocs](https://docs.unity3d.com/ScriptReference/TransformUtils.html)

