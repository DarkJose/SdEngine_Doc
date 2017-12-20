//设定**窗口**的属性

```java
public static void main(String[] args) throws IOException {
        // 窗口创建与设定
        JFrame frame = new MainPage();
        music = loadMusic("src/music/a.wav");
        frame.setTitle("推箱子");
        frame.setUndecorated(false);
        frame.pack();
        frame.setVisible(true);
    }
```



