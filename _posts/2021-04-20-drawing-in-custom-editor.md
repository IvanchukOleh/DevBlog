---
layout: post
visible: 1
title: "Drawing in CustomEditor"
categories: [Unity]
tags: [unity, editor, tip]
author: Matanist
---

* content
{:toc}

## Завдання
Інколи звичних полів інспектора не вистачає і треба краще візуалізувати дані. Наприклад, намалювати графік, чи будь-що
інше. В цьому допоможе низькорівнева графічна бібліотека UnityEngine.GL.





## Використання
Для малювання у власному редакторі потрібно перевантажити метод OnInspectorGUI. Послідовність дій така:

- ```OnEnable()```
    - створення матеріалу з відповідним шейдером;
- ```OnDisable()```
    - видалення матеріалу;
- ```OnInspectorGUI()```
    - визначення розмірів області для малювання;
    - відкриття області для малювання;
    - збереження поточних матриць ```model```, ```view```, ```projection``` вгорі стеку матриць;
    - очищення області малювання;
    - застосування відповідного шейдера до матеріалу;
    - власне, малювання;
    - відновлення збережених матриць ```model```, ```view```, ```projection``` зі стеку матриць;
    - закриття області для малювання.

## Приклад
Малювання системи координат висотою 200 пікселів із лінійним графіком:

![Example](/assets/2021-04-20-drawing-in-custom-editor-0.png)

```c#
//...
private readonly Color _backgroundColor = Color.grey;
private readonly Color _axisColor = new Color(0.6f, 0.6f, 0.6f, 1);
private readonly Color _linesColor = new Color(0.1f, 0.1f, 0.1f, 1);

private Material _material;

private void OnEnable() {
    //...
    Shader shader = Shader.Find("Hidden/Internal-Colored");
    _material = new Material(shader);
}

private void OnDisable() {
    DestroyImmediate(_material);
}

public override void OnInspectorGUI() {
    //визначення розмірів області для малювання. 
    //Перші два параметри (ширина) тут ігноруються:
    Rect rect = GUILayoutUtility.GetRect(200, 200, 200, 200);
    //блок фіксованої ширини з вирівнюванням по лівому краю:
    //EditorGUILayout.BeginHorizontal();
    //Rect rect = GUILayoutUtility.GetRect(200, 200, 200, 200);
    //...
    //GUILayout.FlexibleSpace();
    //EditorGUILayout.EndHorizontal();
    
    Vector2 center = new Vector2(rect.width * 0.5f, rect.height * 0.5f);

    //OnInspectorGUI викликається дещо частіше, ніж перемальовується редактор, 
    //тому потрібна додаткова перевірка:
    if (Event.current.type == EventType.Repaint) {
        //відкриття області для малювання. 
        //Початок координат у верхньому лівому куті
        GUI.BeginClip(rect);
        //збереження поточних матриць
        GL.PushMatrix();
        //очищення поля
        GL.Clear(true, false, Color.black);
        //застосування відповідного шейдера
        _material.SetPass(0);

        //фон
        //Для малювання прямокутника використовується привітив "квад" (GL.QUADS).
        //Кожні 4 послідовні точки, передані через GL.Vertex3 утворюють окремий квад.
        GL.Begin(GL.QUADS);
        GL.Color(_backgroundColor);
        GL.Vertex3(0, 0, 0);
        GL.Vertex3(rect.width, 0, 0);
        GL.Vertex3(rect.width, rect.height, 0);
        GL.Vertex3(0, rect.height, 0);
        GL.End();
        
        //для малювання ліній використовується примітив "лінія" (GL.LINES).
        //Кожна пара точок, передана через GL.Vertex3 утворює лінію
        GL.Begin(GL.LINES);        
        GL.Color(_axisColor);
        // OX
        GL.Vertex3(0, center.y, 0);
        GL.Vertex3(rect.width, center.y, 0);
        // OY
        GL.Vertex3(center.x, 0, 0);
        GL.Vertex3(center.x, rect.height, 0);
        GL.End();

        //лінія з лівого нижнього кута в правий верхній
        GL.Begin(GL.LINES);
        GL.Color(_linesColor);
        GL.Vertex3(0, rect.height, 0);
        GL.Vertex3(rect.width, 0, 0);
        GL.End();

        //відновлення значень матриць
        GL.PopMatrix();
        //закриття області для малювання
        GUI.EndClip();
    }
}
```

## Корисні посилання:
- [UnityDocs, UnityEngine.GL](https://docs.unity3d.com/ScriptReference/GL.html)  
- [UnityDocs, UnityEngine.GL.PopMatrix](https://docs.unity3d.com/ScriptReference/GL.PopMatrix.html)  
- [UnityDocs, UnityEngine.GL.PushMatrix](https://docs.unity3d.com/ScriptReference/GL.PushMatrix.html)  
- [UnityDocs, EventType.Repaint](https://docs.unity3d.com/ScriptReference/EventType.Repaint.html)  
- [UnityAnswers, How to draw lines in a custom Inspector](https://answers.unity.com/questions/1360515/how-do-i-draw-lines-in-a-custom-inspector.html)  