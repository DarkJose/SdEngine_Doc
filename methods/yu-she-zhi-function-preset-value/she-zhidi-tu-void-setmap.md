//初始化地图，包括各类**对象**的初始化，详见代码**注释**

```java
    public static void setMap() {
        // 创建物理运算
        new NormalPhysics("标准物理");
        // 命名动画
        cloneAnimateAct("fox", "下", "1");
        cloneAnimateAct("fox", "左下", "2");
        cloneAnimateAct("fox", "左", "3");
        cloneAnimateAct("fox", "左上", "4");
        cloneAnimateAct("fox", "上", "5");
        cloneAnimateAct("fox", "右上", "6");
        cloneAnimateAct("fox", "右", "7");
        cloneAnimateAct("fox", "右下", "stand");
        // 读取地图
        File root = new File("map");
        File[] files = root.listFiles();
        for (File file : files) {
            try {
                BufferedReader reader = new BufferedReader(new FileReader(file));
                String tempString = null;
                while ((tempString = reader.readLine()) != null)
                    if (maps.get(file.getName()) == null)
                        maps.put(file.getName(), tempString);
                    else
                        maps.put(file.getName(), maps.get(file.getName()) + ":" + tempString);
                reader.close();
            } catch (IOException e) {
            }
        }
        // 生成地图
        int mapNum = -1;
        Enumeration<String> mapsKey = maps.keys();
        while (mapsKey.hasMoreElements()) {
            String key = mapsKey.nextElement();
            String map = maps.get(key);
            String last = "", aim = "";
            int line = 0;
            mapNum++;
            Api.createDialog(1850, 200 + -150 + mapNum * 150, mapNum + "", the("show"));
            Api.createChat(-5, 5, mapNum + "");
            Api.addChat(mapNum + "", mapNum + 1 + "");
            dialog(mapNum + "").textColor = Color.DARK_GRAY;
            while (!last.contentEquals(map)) {
                if (line == 0) {
                    aim = map.substring(0, 1);
                    last = map.substring(map.indexOf(":") + 1);
                } else {
                    if (last.indexOf(":") != -1) {
                        aim = last.substring(0, last.indexOf(":"));
                        last = last.substring(last.indexOf(":") + 1);
                    } else {
                        aim = last;
                        last = map;
                    }
                }
                if (aim.length() == 1)
                    create(mapNum * 1920 + 664, 605, degree(270), aim + key, defaultAct, the("map" + aim));
                else {
                    for (int i = 0; i < aim.length(); i++) {
                        if (aim.substring(i, i + 1).contentEquals("1")) {
                            create(mapNum * 1920 + i * 128, line * 128, degree(270),
                                    "石头" + i * 100 + line + mapNum * 10000, defaultAct, the("castle"));
                            unit("石头" + i * 100 + line + mapNum * 10000).collision = new Collision.RoundCollision(80);
                            unit("石头" + i * 100 + line + mapNum * 10000).collision.passable = false;
                        }
                        if (aim.substring(i, i + 1).contentEquals("2")) {
                            create(mapNum * 1920 + i * 128, line * 128, degree(270),
                                    "箱子" + i * 100 + line + mapNum * 10000, defaultAct, the("boxx"));
                            unit("箱子" + i * 100 + line + mapNum * 10000).collision = new Collision.RoundCollision(30);
                            unit("箱子" + i * 100 + line + mapNum * 10000).collision.passable = false;
                            unit("箱子" + i * 100 + line + mapNum * 10000).animateSpeed = 20;
                            physics("标准物理").add("箱子" + i * 100 + line + mapNum * 10000);
                        }
                        if (aim.substring(i, i + 1).contentEquals("3")) {
                            create(mapNum * 1920 + i * 128, line * 128, degree(270),
                                    "目标" + i * 100 + line + mapNum * 10000, defaultAct, the("aim"));
                            unit("目标" + i * 100 + line + mapNum * 10000).collision = new Collision.RoundCollision(80);
                            unit("目标" + i * 100 + line + mapNum * 10000).collision.passable = false;
                        }
                        if (aim.substring(i, i + 1).contentEquals("4")) {
                            mainPos[mapNum] = new Vector2();
                            mainPos[mapNum].x = mapNum * 1920 + i * 128;
                            mainPos[mapNum].y = line * 128;
                            if (mapNum == 0) {
                                create(i * 128, line * 128, degree(270), "主角", Implement.defaultAct, the("fox"));
                                unit("主角").collision = new Collision.RoundCollision(30);
                                physics("标准物理").add("主角");
                            }
                        }
                    }
                }
                line++;
            }
        }
        // 创建对话框
        Api.createDialog(860, 540, "菜单", the("show2"));
        Api.createChat(0, 0, "菜单");
        Api.addChat("菜单", "");
        // 设定镜头位置
        MainPage.cameraX = 600;
        MainPage.cameraY = 600;
    }
```



