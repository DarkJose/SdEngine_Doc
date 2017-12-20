//每0.03秒调用一次，可在MainPage.java控制刷新速度，控制主逻辑与按键效果绑定

```java
	public static void fixedUpdate() {
		// 初始状态逻辑
		if (keyPressedConfirm(KeyEvent.VK_W) || keyPressedConfirm(KeyEvent.VK_S)) {
			ibox = ~ibox;
		}
		if (keyPressed(Implement.keyDo) && ibox == 0 && GameState == 0) {
			GameState = 1;
			hideDialog("菜单");
			cameraMoveTo(600, 600, 1, timeSpan);
		} else if (keyPressed(Implement.keyDo) && ibox == -1 && GameState == 0) {
			System.exit(0);
		}
		// 记录变化信息
		if (noDragging)
			if (!mainPosition.equals(unit("主角").pos)) {
				mainPosition.set(unit("主角").pos);
				for (GameObject one : allGameObjects()) {
					if (one.animateSource.equals(the("boxx")) || one.animateSource.equals(the("fox"))
							|| one.animateSource.equals(the("old"))) {
						source.put(time + ":" + one.name, one.animateSource);
						position.put(time + ":" + one.name, new Vector2(one.x, one.y));
						dact.put(time + ":" + one.name, one.defaultAct);
						calculDir.put(time + ":" + one.name, one.calculDir);
						act.put(time + ":" + one.name, one.thisAct);
						frame.put(time + ":" + one.name, one.animateFrame);
					}
				}
			}
		// 将单位角度与按键和动作关联
		if (GameState == 1) {
			unit("主角").calculDir = 0;
			if (keyPressed(Implement.keyUp))
				unit("主角").calculDir += 3;
			if (keyPressed(Implement.keyDown))
				unit("主角").calculDir -= 3;
			if (keyPressed(Implement.keyLeft))
				unit("主角").calculDir -= 1;
			if (keyPressed(Implement.keyRight))
				unit("主角").calculDir += 1;
			if (unit("主角").calculDir != 0) {
				switch (unit("主角").calculDir) {
				case 4:
					unit("主角").thisAct = "右上";
					unit("主角").defaultAct = "右上";
					break;
				case 1:
					unit("主角").thisAct = "右";
					unit("主角").defaultAct = "右";
					break;
				case -2:
					unit("主角").thisAct = "右下";
					unit("主角").defaultAct = "右下";
					break;
				case -3:
					unit("主角").thisAct = "下";
					unit("主角").defaultAct = "下";
					break;
				case -4:
					unit("主角").thisAct = "左下";
					unit("主角").defaultAct = "左下";
					break;
				case -1:
					unit("主角").thisAct = "左";
					unit("主角").defaultAct = "左";
					break;
				case 2:
					unit("主角").thisAct = "左上";
					unit("主角").defaultAct = "左上";
					break;
				case 3:
					unit("主角").thisAct = "上";
					unit("主角").defaultAct = "上";
					break;
				}
			}
		}
	}
```



