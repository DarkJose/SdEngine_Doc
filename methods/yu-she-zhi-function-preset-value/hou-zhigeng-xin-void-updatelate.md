//在每次图像绘制后调用，可显示在对话框之上，亦可用于碰撞运算

```java
    public static void updateLate(Graphics bg) {
        // 绘制在最上层
        if (time > 18 && GameState == 0) {
            bg.drawString("Start", 815, 613);
            bg.drawString("Exit", 819, 643);
            if (ibox == 0) {
                bg.drawImage(the("box", defaultAct, 0), 785, 595, null);
            } else {
                bg.drawImage(the("box", defaultAct, 0), 785, 625, null);
            }
        }
        // 双重碰撞计算
        GameObject object = unit("主角");
        Enumeration<String> collisionObject = gameObject.keys();
        while (collisionObject.hasMoreElements()) {
            GameObject object2 = gameObject.get(collisionObject.nextElement());
            if (!object.hidden && !object2.hidden && !object.equals(object2) && object.collision != null
                    && object2.collision != null) {
                if (Api.collision(object, object2))
                    Implement.collision(object, object2);
            }
        }
    }
```



