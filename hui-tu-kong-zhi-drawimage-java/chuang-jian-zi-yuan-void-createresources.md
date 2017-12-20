//

```java
	private void createResources(String filePath) {
		File root = new File(filePath);
		File[] files = root.listFiles();
		for (File file : files)
			if (file.isDirectory()) {
				animateObject.put(file.getName(), new AnimateObject());
				createResources(file.getAbsolutePath());
			} else if (getParentName(file).contentEquals("image")) {
				animateObject.put(deleteSuffix(file.getName()), new AnimateObject());
				setAnimateAct(deleteSuffix(file.getName()), Implement.defaultAct,
						new Api().getAbsoluteImage(file.getAbsolutePath()));
			} else {
				if (the(getParentName(file)).act.size() == 0 || the(getParentName(file)).act.size() == 1) {
					setAnimateAct(getParentName(file), Implement.defaultAct,
							new Api().getAbsoluteImage(file.getAbsolutePath()));
				} else
					setAnimateAct(getParentName(file), Integer.toString(the(getParentName(file)).act.size() - 1),
							new Api().getAbsoluteImage(file.getAbsolutePath()));
				if (!intToFile(getParentName(file), fileToInt(file) + 1).exists())
					setAnimateAct(getParentName(file), Integer.toString(the(getParentName(file)).act.size()));
			}
	}
```



