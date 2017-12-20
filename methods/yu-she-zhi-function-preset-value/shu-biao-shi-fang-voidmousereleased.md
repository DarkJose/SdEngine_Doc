//此处用于配合**鼠标拖动**事件

```java
public static void mouseReleased(MouseEvent e) {
        noDragging = true;
        mapNoDragging = true;
        for (GameObject one : allGameObjects())
            one.stopAct = false;
    }
```



