//**游戏对象**产生**碰撞**后将会使信息传递至此

```java
    public static void collision(GameObject a, GameObject b) {
        if (objectAnimate(a, b, "fox", "boxx")) {
            if (a.animateSource.equals(the("boxx"))) {
                if (Math.abs(b.calculDir % 2) != 0)
                    a.calculDir = b.calculDir;
            } else {
                if (Math.abs(a.calculDir % 2) != 0)
                    b.calculDir = a.calculDir;
            }
        }
        if (objectAnimate(a, b, "aim", "boxx")) {
            if (a.animateSource.equals(the("boxx"))) {
                a.animateSource(the("old"));
                move(a, 256 * 10, timeSpan);
            } else {
                b.animateSource(the("old"));
                move(b, 256 * 10, timeSpan);
            }
        }
    }
```



