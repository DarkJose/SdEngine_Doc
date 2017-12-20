//

```java
	public void paint(Graphics g) {
		BufferedImage bf = new BufferedImage(Implement.DesignWidth, Implement.DesignHeight, 2); // 缓冲图片
		Graphics bg = bf.createGraphics(); // 缓冲图片的graphics对象
		Implement.updateEarly(bg);
		Enumeration<String> dKeys = dialogObject.keys();
		while (dKeys.hasMoreElements()) {
			DialogObject object = dialogObject.get(dKeys.nextElement());
			if (!object.hidden) {
				bg.drawImage(object.animate(), (int) (object.x + object.imageOffset.x),
						(int) (object.y + object.imageOffset.y), null);
				if (!object.contentObject.hidden) {
					bg.setFont(new Font(dialog(object).textFormat, dialog(object).textStyle, dialog(object).textSize));
					bg.setColor(dialog(object).textColor);
					bg.drawString(dialog(object).dialogContent.get(dialog(object).dialogIndex),
							(int) (object.x + dialog(object).x), (int) (object.y + dialog(object).y));
				}
			}
		}
		Implement.updateLate(bg);
		g.drawImage(bf, 0, 0, null);
		repaint();
	}
```



