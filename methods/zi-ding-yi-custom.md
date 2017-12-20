//内容逻辑的自定义变量

//关卡选择区坐标

public static Vector2 **showPos **= new Vector2\(\);

//各关卡主角所在坐标

public static Vector2\[\] **mainPos **= new Vector2\[100\];

//记录音乐

public static Clip **music**;

//是否在拖动**回退**，**音乐**是否开启

public static boolean **noDragging **= true, musicStart;

//是否在拖动**关卡**

public static boolean **mapNoDragging **= true;

//游戏状态

public static int **GameState **= 0;

//菜单当前选项

public static int **ibox** = 0;

//下为记录变化信息变量，用于**回退**

public static Vector2 **mainPosition **= new Vector2\(\);

public static Hashtable&lt;String, AnimateObject&gt; **source **= new Hashtable&lt;String, AnimateObject&gt;\(\);

public static Hashtable&lt;String, Vector2&gt; **position **= new Hashtable&lt;String, Vector2&gt;\(\);

public static Hashtable&lt;String, Integer&gt; **calculDir **= new Hashtable&lt;String, Integer&gt;\(\);

public static Hashtable&lt;String, String&gt; **dact **= new Hashtable&lt;String, String&gt;\(\);

public static Hashtable&lt;String, String&gt; **act **= new Hashtable&lt;String, String&gt;\(\);

public static Hashtable&lt;String, Integer&gt; **frame **= new Hashtable&lt;String, Integer&gt;\(\);

public static Hashtable&lt;String, String&gt; **maps **= new Hashtable&lt;String, String&gt;\(\);

