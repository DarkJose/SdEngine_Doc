//**鼠标拖动**事件，一般与**鼠标按下**和**鼠标释放**事件共同作用

```java
    public static void mouseDragged(MouseEvent e) {
        //连续式退步，根据时间线排序后同步时间线
        if (!noDragging) {
            List<Map.Entry<String, Vector2>> list = new ArrayList<Map.Entry<String, Vector2>>(position.entrySet());
            Collections.sort(list, new Comparator<Map.Entry<String, Vector2>>() {
                public int compare(Entry<String, Vector2> arg0, Entry<String, Vector2> arg1) {
                    return Integer.parseInt(arg0.getKey().substring(0, arg0.getKey().indexOf(':')))
                            - Integer.parseInt(arg1.getKey().substring(0, arg1.getKey().indexOf(':')));
                }
            });

            int i = 0;
            while (i < list.size()) {
                String x = list.get(i).getKey();
                if (x.substring(x.indexOf(':') + 1).contentEquals("主角")) {
                    if (((float) e.getX() - 1650) / (1850 - 1650) * position.size() <= i) {
                        for (GameObject one : allGameObjects()) {
                            one.stopAct = true;
                            String k = x.substring(0, x.indexOf(':') + 1) + one.name;
                            if (position.containsKey(k)) {
                                one.animateSource = source.get(k);
                                one.pos(position.get(k));
                                one.defaultAct = dact.get(k);
                                one.calculDir = calculDir.get(k);
                                one.thisAct = act.get(k);
                                one.animateFrame = frame.get(k);
                            }
                        }
                        break;
                    }
                }
                i++;
            }
        }
        //关卡拖动
        if (!mapNoDragging) {
            Enumeration<String> objects = dialogObject.keys();
            while (objects.hasMoreElements()) {
                DialogObject object = dialogObject.get(objects.nextElement());
                if (object.animateSource.equals(the("show")))
                    object.y += (e.getY() - showPos.y) / 10;
            }
        }

    }
```



