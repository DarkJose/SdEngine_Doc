public static float **cameraX**, **cameraY**;

public static int **CellX **= \(int\) Implement.DesignWidth / 128 + 3;

public static int **CellY **= \(int\) Implement.DesignHeight / 128 + 3;

public static int **timeSpan **= 30, **time **= 0, **interval **= 5; // each interval is 0.03s\(timeSpan/1000\)

public static Timer **GlobalTimer **= new Timer\(\);

public static Hashtable&lt;Object, Timer&gt; **KeyPressedConfirmTimer **= new Hashtable&lt;Object, Timer&gt;\(\);

public static Hashtable&lt;Object, Boolean&gt; **KeyPressedFirst **= new Hashtable&lt;Object, Boolean&gt;\(\);

public static Hashtable&lt;Object, Boolean&gt; **KeyPressed **= new Hashtable&lt;Object, Boolean&gt;\(\);

public static Hashtable&lt;Object, Boolean&gt; **KeyPressedConfirm **= new Hashtable&lt;Object, Boolean&gt;\(\);

