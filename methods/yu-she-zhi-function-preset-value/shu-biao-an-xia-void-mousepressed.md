//**鼠标按下**事件，因为比**鼠标点击**事件更敏感，因而使用此来代替各类按钮点击

```java
    public static void mousePressed(MouseEvent e) {
        //音乐
        if (clickIn(e, new Vector2(50, 50), new Vector2(100, 100))) {
            if (musicStart) {
                musicStart = !musicStart;
                music.stop();
            } else if (!musicStart) {
                musicStart = !musicStart;
                music.start();
            } else {
                musicStart = true;
                music.start();
            }
        }
        //连续式退步
        if (clickIn(e, new Vector2(1650, 900), new Vector2(1850, 950))) {
            noDragging = false;
        }
        if (clickIn(e, new Vector2(1850, 0), new Vector2(1950, 900))) {
            mapNoDragging = false;
            showPos.set(e.getX(), e.getY());
        }
        //关卡点击
        int i = 0;
        Enumeration<String> objects = dialogObject.keys();
        while (objects.hasMoreElements()) {
            DialogObject object = dialogObject.get(objects.nextElement());
            //关卡定位
            if (object.animateSource.equals(the("show"))) {
                if (clickIn(e, new Vector2(1850, object.y - 50), new Vector2(1950, object.y + 50))) {
                    cameraMoveTo(600 + 1920 * i, 600, 0.5f, timeSpan);
                    List<Map.Entry<String, Vector2>> list = new ArrayList<Map.Entry<String, Vector2>>(
                            position.entrySet());
                    Collections.sort(list, new Comparator<Map.Entry<String, Vector2>>() {
                        public int compare(Entry<String, Vector2> arg0, Entry<String, Vector2> arg1) {
                            return Integer.parseInt(arg0.getKey().substring(0, arg0.getKey().indexOf(':')))
                                    - Integer.parseInt(arg1.getKey().substring(0, arg1.getKey().indexOf(':')));
                        }
                    });
                    for (GameObject one : allGameObjects()) {
                        String k = position.keys().nextElement().substring(0,
                                position.keys().nextElement().indexOf(":") + 1) + one.name;
                        if (position.containsKey(k)) {
                            one.animateSource = source.get(k);
                            one.pos(position.get(k));
                            one.defaultAct = dact.get(k);
                            one.calculDir = calculDir.get(k);
                            one.thisAct = act.get(k);
                            one.animateFrame = frame.get(k);
                        }
                    }
                    //换关后清空退步
                    unit("主角").pos(mainPos[i]);
                    source.clear();
                    position.clear();
                    dact.clear();
                    calculDir.clear();
                    act.clear();
                    frame.clear();
                }
                i++;
            }
        }
    }
```



