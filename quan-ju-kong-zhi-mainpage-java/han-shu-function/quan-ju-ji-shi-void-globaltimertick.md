//

```java
	private void globalTimerTick() {
		time++;
		Implement.fixedUpdate();

		Enumeration<String> PKeys = PhysicsObject.physicsObject.keys();
		while (PKeys.hasMoreElements()) {
			PKeys.nextElement();
			for (PhysicsObject one : allPhysicsObjects())
				one.run();
		}

		Enumeration<Object> keys = KeyPressedConfirm.keys();
		while (keys.hasMoreElements()) {
			int thisKey = (int) keys.nextElement();
			if (keyPressedConfirm(thisKey)) {
				KeyPressedConfirm.put(thisKey, false);
				KeyPressedConfirmTimer.put(thisKey, new Timer());
				KeyPressedConfirmTimer.get(thisKey).schedule(new TimerTask() {
					public void run() {
						KeyPressedConfirmTick(thisKey);
					}
				}, MainPage.timeSpan * MainPage.interval);
			}
		}
	}
```



