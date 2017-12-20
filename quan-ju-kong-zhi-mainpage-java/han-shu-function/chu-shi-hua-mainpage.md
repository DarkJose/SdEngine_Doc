//

```java
	public MainPage() throws IOException {
		DrawImage panel = new DrawImage();
		this.add(panel);
		this.addWindowListener(new WindowAdapter() {
			public void windowClosing(WindowEvent e) {
				System.exit(0);
			}
		});
		Implement.setMap();
		GlobalTimer.schedule(new TimerTask() {
			public void run() {
				globalTimerTick();
			}
		}, 0, timeSpan);
	}
```



