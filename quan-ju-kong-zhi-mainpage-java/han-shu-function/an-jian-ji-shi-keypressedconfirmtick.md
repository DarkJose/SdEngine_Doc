//

```java
    private void keyPressedConfirmTick(int sender) {
        if (keyPressed(sender))
            MainPage.KeyPressedConfirm.put(sender, true);
        KeyPressedConfirmTimer.get(sender).cancel();
    }
```



