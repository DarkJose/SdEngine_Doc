//

```java
	public DrawImage() {
		String filePath = "src/image";
		createResources(filePath);
		setFocusable(true);
		setPreferredSize(new Dimension(Implement.DesignWidth, Implement.DesignHeight));
		addKeyListener(new KeyAdapter() {
			public void keyPressed(KeyEvent e) {
				KeyPressed.put(e.getKeyCode(), true);
				if (KeyPressedFirst.getOrDefault(e.getKeyCode(), true)) {
					KeyPressedConfirm.put(e.getKeyCode(), true);
					KeyPressedFirst.put(e.getKeyCode(), false);
				}
			}

			public void keyReleased(KeyEvent e) {
				KeyPressed.put(e.getKeyCode(), false);
				KeyPressedFirst.put(e.getKeyCode(), true);
				KeyPressedConfirm.put(e.getKeyCode(), false);
			}
		});
		addMouseListener(new MouseAdapter()// 鼠标监听
		{
			public void mouseClicked(MouseEvent e) {
				Implement.mouseClicked(e);
			}

			public void mousePressed(MouseEvent e) {
				Implement.mousePressed(e);
			}

			public void mouseReleased(MouseEvent e) {
				Implement.mouseReleased(e);
			}
		});
		addMouseMotionListener(new MouseAdapter()// 鼠标监听
		{
			public void mouseMoved(MouseEvent e) {
				Implement.mouseMoved(e);
			}

			public void mouseDragged(MouseEvent e) {
				Implement.mouseDragged(e);
			}
		});

	}
```



