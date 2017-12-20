//在每次图像绘制前调用，主要用于控制绘制层次关系

```java
    public static void updateEarly(Graphics bg) {
        // 绘制层次控制
        if (dialogObject.get("菜单").animateFrame == dialogObject.get("菜单").animateSource.act.get("stand").size() - 1)
            dialogObject.get("菜单").stopAct = true;
        levelDraw("map1", bg);
        levelDraw("map2", bg);
        levelDraw("map3", bg);
        levelDraw("castle", bg);
        levelDraw("aim", bg);
        levelDraw("boxx", bg);
        levelDraw("old", bg);
        levelDraw("fox", bg);
        bg.drawString("回退", 1650, 890);
        bg.drawRect(1650, 900, 200, 50);
        bg.drawRect(1800, 0, 100, 900);
        bg.drawString("音乐", 50, 40);
        bg.drawRect(50, 50, 50, 50);
    }
```



