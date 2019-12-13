# photoTest
Android开发规范

一、名词解释

【强制】：必须按照规范执行
【建议】：建议按照规范执行，可根据特殊情景来决定
【Review】：提交代码前需被review
二、Java/Kotlin
1.命名风格
【强制】1.1 代码中的命名严禁以下划线或美元符号开始和以下划线或美元符号结束
【强制】1.2 严禁使用拼音与英文结合（国际通用拼音类名称可视为英文）
【强制】1.3 类名使用大写驼峰命名法，如：UserInfo
【强制】1.4 方法名、参数名、成员变量、局部变量统一使用小写驼峰命名法，如：localValue、getMessage（）
【强制】1.5 非public，非static的变量名以m开头（kotlin中companion object内部变量也参照此规则），视图控件声明以小写v开头，static的变量名以s开头，其它field以小写字母开头
【强制】1.6 常量命名全部大写，单词间用下划线分隔，力求语义表达表达完整清晰，长也没事，如：MAX_STOCK_COUNT
【强制】1.7 抽象类使用Abstract开头，接口以大写I开头，异常类使用Exception结尾，测试类以它需要测试的类名开头，Test结尾
【强制】1.8 数组使用类型与中括号相连来声明，如：int[] array
【强制】1.9 包名统一使用小写，点分隔符之间有且只有一个自然语义单词，包名统一使用单数形式
【建议】1.10 如果模块、接口、类、方法使用了设计模式，在命名时需要体现出具体模式，如：public class OrderFactory；public class LoginObserver
【强制】1.11 接口类中方法与属性不要加任何修饰符号（public也不要加）
【强制】1.12 枚举类名建议带上Enum后缀，枚举成员名称需要全大写，单词间用下划线隔开
【强制】1.13 POJO中设置/获取单个对象方法用set/get做前缀，设置/获取多个对象用set/get做前缀List结尾，形如：set/getXXXList
【强制】1.14 DAO获取统计值方法用count做前缀，插入方法用insert做前缀，删除用delete做前缀，修改方法用update做前缀
【强制】1.15 数组以Array结尾、集合以List结尾、Map以Map结尾、实体类以Entity结尾、工具类以Util结尾
2.变/常量定义
【强制】2.1 禁止出现魔法值（即未经预先定义的常量）直接出现在代码中，如：String key=“Id#taobao_”+tradeId
【强制】2.2 声明long或Long类型时，必须以大写L结尾，float类型以小写f结尾，十六进制必须补全
【强制】2.3 不要使用一个常量类维护所有常量，要按常量功能进行归类，分开维护，大而全的常量类杂乱无章，要使用查找功能才能定位到常量，不利于理解与维护
【建议】2.4 Kotlin中建议使用类型推导声明变量
3.代码格式
【建议】3.1 if/for/while/switch/do 等保留字与括号之间都必须加空格
【建议】3.2 任何二目、三目运算符的左右两边都需要加一个空格
【建议】3.3 采用 4 个空格缩进，禁止使用 tab 字符
【建议】3.4 注释的双斜线与注释内容之间有且仅有一个空格
【建议】3.5 方法参数在定义和传入时，多个参数逗号后边必须加空格，如：method(args1, args2, args3)
【建议】3.6 单个方法的总行数建议不超过 80 行，分清方法主要作用
【强制】3.7 统一使用注释、格式化等模板
4.OOP规约
【强制】4.1 禁止通过一个类的对象引用访问此类的静态变量或静态方法，无谓增加编译器解析成本，直接用类名来访问即可
【强制】4.2 所有的覆写方法，必须加@Override 注解，如：getObject()与 get0bject()的问题。一个是字母的 O，一个是数字的 0，加@Override 可以准确判断是否覆盖成功。另外，如果在抽象类中对方法签名进行修改，其实现类会马上编译报错。
【建议】4.3 相同参数类型，相同业务含义，才可以使用 Java 的可变参数，避免使用 Object
【强制】4.4 编写sdk时禁止任意修改方法名，如果废弃方法名必须加@Deprecated 注解，并清晰地说明采用的新接口
【强制】4.5 Object 的 equals 方法容易抛空指针异常，应使用常量或确定有值的对象来调用 equals，可使用Objects或TextUtils的equal方法
【强制】4.6 使用索引访问用 String 的 split 方法得到的数组时，需做最后一个分隔符后有无内容的检查，否则会有抛IndexOutOfBoundsException 的风险，如：String str = "a,b,c,,";String[] ary = str.split(","); // 预期大于 3，结果是 3 
【建议】4.7 一个类有多个构造方法，或者多个同名方法，这些方法应该按顺序放置在一起， 便于阅读
【强制】4.8 类内方法定义的顺序依次是:公有方法或保护方法 > 私有方法 > getter/setter方法
【强制】4.9 慎用 Object 的 clone 方法来拷贝对象，因为其本身只是浅拷贝
【强制】4.10 类成员与方法访问控制从严
【强制】4.11 代码中禁止硬编码，如是用于Logcat输出、异常信息可直接编写并仅限于英文
【强制】4.12 错误弹窗提示应简洁明了，不要加入感叹号
【强制】4.13 Kotlin中字符串连接使用字符串模板实现，禁止使用+连接
【建议】4.14 Kotlin中禁止使用双感叹号!!来表述变量为非空对象，避免出现KotlinNullPointerException
【强制】4.15 Lambda表达式回调方法里的形参如果用不到，则将形参名称改为下划线“_”
5.集合处理
【强制】5.1 关于 hashCode 和 equals 的处理，遵循如下规则:
【强制】5.1.1 只要重写equals，就必须重写hashCode
【强制】5.1.2 因为Set存储的是不重复的对象，依据hashCode和equals进行判断，所以Set存储的 对象必须重写这两个方法
【强制】5.1.3 如果自定义对象作为Map的键，那么必须重写hashCode和equals
说明:String 重写了 hashCode 和 equals 方法，所以我们可以非常愉快地使用 String 对象 作为 key 来使用

【强制】5.2 ArrayList的subList结果不可强转成ArrayList，否则会抛出ClassCastException 异常 
【强制】5.3 注意Map类集合K/V能不能存储null值情况，如下表格： 

集合类 
Key 
Value 
Super 
说明 
Hashtable
不允许为null
不允许为null
Dictionary
线程安全
ConcurrentHashMap
不允许为null
不允许为null
AbstractMap
锁分段技术
TreeMap
不允许为null
允许为null
AbstractMap
非线程安全
HashMap
允许为null
允许为null
AbstractMap
非线程安全
【强制】5.4 利用 Set 元素唯一的特性，可以快速对一个集合进行去重操作，避免使用 List 的 contains 方法进行遍历、对比、去重操作
 6.并发处理
【强制】6.1 多线程情况下获取单例对象强制保证线程安全
【建议】6.2 创建线程或线程池时建议指定有意义的线程名称，方便出错时回溯
【建议】6.3 线程资源建议通过线程池提供（特殊情况可自行显式创建单例线程），如果不使用线程池，有可能造成系统创建大量同类线程而导致消耗完内存或 者“过度切换”的问题
【强制】6.4 线程池不允许使用 Executors 去创建，而是通过自定义ThreadPoolExecutor 的方式，这样的处理方式让写的同学更加明确线程池的运行规则，规避资源耗尽的风险
Executors 返回的线程池对象的弊端如下：
FixedThreadPool 和 SingleThreadPool:允许的请求队列长度为 Integer.MAX_VALUE，可能会堆积大量的请求，从而导致 OOM
CachedThreadPool 和 ScheduledThreadPool:允许的创建线程数量为 Integer.MAX_VALUE，可能会创建大量的线程，从而导致 OOM
【强制】6.5 SimpleDateFormat 是线程非安全的类，一般不要定义为static变量，如果定义为static，必须加锁，或者使用 DateUtils 工具类，如果使用JDK8，可以使用 Instant 代替 Date，LocalDateTime 代替 Calendar， DateTimeFormatter 代替 SimpleDateFormat
【强制】【Review】6.6 高并发时，同步调用应该去考量锁的性能损耗。能用无锁数据结构，就不要用锁;能 锁区块，就不要锁整个方法体;能用对象锁，就不要用类锁
【强制】6.7 在高并发场景中，避免使用”等于”判断作为中断或退出的条件，尽量使用大于或小于某一值判断
7.控制语句
【强制】7.1 在一个 switch 块内，每个 case 要么通过 break/return 等来终止，要么注释说明程 序将继续执行到哪一个 case 为止;在一个 switch 块内，都必须包含一个 default 语句并且 放在最后，即使空代码
【强制】7.2 在 if/else/for/while/do 语句中必须使用大括号。即使只有一行代码，避免采用 单行的编码方式:if (condition) statements
【建议】7.3 表达异常的分支时，少用 if-else 方式，这种方式可以改写成:
if (condition) {
...
return obj;
}
如果非得使用 if()...else if()...else...方式表达逻辑，避免后续代码维护困难，请勿超过 3 层 ，超过 3 层的 if-else 的逻辑判断代码可以使用卫语句、策略模式、状态模式等来实现， 其中卫语句示例如下:
public void today() {
  if (isBusy()) {
 System.out.println(“change time.”); 
 return;
 }
 if (isFree()) {
 System.out.println(“go to travel.”);
 return;
 }
 System.out.println(“stay at home to learn Alibaba Java Coding Guidelines.”);
 return;
 }
【强制】7.4 循环体中的语句要考量性能，以下操作尽量移至循环体外处理，如定义对象（尽量重用已定义对象）、变量、获取数据库连接、 try-catch 操作
【建议】7.5 Kotlin中使用forEach语法（性能较一般循环好）

8.注释规约
【强制】8.1 类、类属性、类方法的注释必须使用 Javadoc 规范，使用/**内容*/格式，不得使用// xxx方式
【强制】8.2 所有的抽象方法(包括接口中的方法)必须要用 Javadoc 注释、除了返回值、参数、 异常说明外，还必须指出该方法做什么事情，实现什么功能
【强制】8.3 所有的类都必须添加创建者和创建日期
【强制】8.4 方法内部单行注释，在被注释语句上方另起一行，使用//注释。方法内部多行注释使用/* */注释，注意与代码对齐
【强制】8.5 所有的枚举类型字段必须要有注释（枚举类上使用多行注释，类内域使用单行注释），说明每个数据项的用途
【强制】8.6 代码修改的同时，注释也要进行相应的修改，尤其是参数、返回值、异常、核心逻辑 等的修改
【强制】8.7 谨慎注释掉代码，在上方详细说明，而不是简单地注释掉。如果无用，则删除
【强制】8.8 对于注释的要求：第一、能够准确反应设计思想和代码逻辑；第二、能够描述业务含 义，使别的程序员能够迅速了解到代码背后的信息。完全没有注释的大段代码对于阅读者形同 天书，注释是给自己看的，即使隔很长时间，也能清晰理解当时的思路;注释也是给继任者看 的，使其能够快速接替自己的工作
【强制】8.9 资源文件注释以大模块划分，不用按Activity页面（资源名称已经将大体模块页面分清楚了）来分太细，页面多了可能注释量比资源名还多，看起来杂乱。如Tab页可按每个Tab来划分后续所有页面
9.异常
【强制】9.1 库中定义的可以通过预检查方式规避的 RuntimeException 异常不应该通过 catch 的方式来处理，应主动抛出异常
【强制】9.2 catch 时请分清稳定代码和非稳定代码，稳定代码指的是无论如何不会出错的代码。 对于非稳定代码的 catch 尽可能进行区分异常类型，再做对应的异常处理，避免做大段代码catch
【强制】9.3 捕获异常是为了处理它，不要捕获了却什么都不处理而抛弃之，如果不想处理它，请 将该异常抛给它的调用者。最外层的业务使用者，必须处理异常，将其转化为用户可以理解的内容
【强制】9.4 finally 块必须对资源对象、流对象进行关闭，有异常也要做 try-catch
【强制】9.5 不要在 finally 块中使用 return，finally 块中的 return 返回后方法结束执行，不会再执行 try 块中的 return 语句
【建议】9.6 方法的返回值可以为 null，不强制返回空集合，或者空对象等
【强制】9.7 Java需使用@Nullable注解标识方法、参数等为可空，注释充分说明什么情况下会返回 null 值
【强制】9.8 防止 NPE，是程序员的基本修养，注意 NPE 产生的场景，可能为null的地方一定要判空
10.日志
【强制】10.1 Logcat输出中禁止使用中文（特殊情况如写入sd卡方便现场工程师查看可携带中文）
三、Android
1.控件/布局缩写
控件/布局 
缩写 
控件/布局 
缩写 
控件/布局 
缩写 
控件/布局 
缩写 
控件/布局 
缩写 
控件/布局 
缩写 
Button
btn
ListView
lv
ImageButton
ib
WebView
wv
SurfaceView
surv
ConstraintLayout
cl
TextView
tv
GridView
gv
RadioGroup
rg
ProgressBar
pb
Spinner
spin


ImageView
iv
RecyclerView
rv
RadioButton
rb
SeekBar
sb
LinearLayout
ll


EditText
et
ScrollView
sv
ToggleButton
tb
VideoView
vv
RelativeLayout
rl


ViewPager
vp
CheckBox
cb
Switch
swit
RatingBar
ratb
FrameLayout
fl


【强制】1.1xml控件id规则：project_module_控件缩写_业务名，自定义控件使用全称小写，如project_module_flexboxlayout_业务名
【强制】1.2 代码中变量声明统一以小写字母v打头，控件/布局全称（自定义控件/布局按自定义名称来）结尾
2.限定词缩写
【强制】控件状态
状态 
缩写 
示例 
正常
normal
sample_normal.png
下压
pressed
sample_pressed.png
选中
checked
sample_checked.png
未选中
unchecked
sample_unchecked.png
有效
enable
sample_enable.png
无效
disable
sample_disable.png
焦点
focused
sample_focused.png
失去焦点
unfocused
sample_unfocused.png
【强制】形状
形状
缩写
圆形
ring
线条
line
方形
rect
椭圆
oval

3.资源文件命名
注：资源文件需带项目名与模块名前缀，具体project名为各自项目名称且名称为全英小写不含特殊字符，具体module名称为各自模块名称且必须为全英小写不含特殊字符，如app_activity
【强制】3.1 Layout
规则：项目名_模块名_类型名[ _item ]
示例：
Activity 的 layout 以 project_module_activity 开头
Fragment 的 layout 以 project_module_fragment 开头
Dialog 的 layout 以project_ module_dialog 开头
include 的 layout 以 project_module_include 开头
ListView 的item layout 以 project_module_list_item 开头
RecyclerView 的 item layout 以 project_module_recycler_item 开头
GridView 的item layout 以 project_module_grid_item 开头
【强制】3.2 Drawable
注：建议只使用一套图，例如：xhdpi
规则：项目名_模块名_业务名_控件缩写_控件状态
示例：
project_module_login_btn_pressed
【强制】3.3 Anim
规则：项目名_模块名_逻辑名称_[方向|序号]
示例：
project_module_fade_in
project_module_loading_grey_001
【强制】3.4 Color
规则：项目名_模块名_aarrggbb，色值统一小写
示例：
<color name="project_module_ffffffff">#ffffffff</color>
【强制】3.5 Dimen
规则：项目名_模块名_sp/dp数值
示例：
project_module_sp14、project_module_dp20
【强制】3.6 Style
规则：项目名_模块名_主题名[.子主题名]，主题名尽量以Theme结尾
示例：
project_app_ParentTheme.ThisActivityTheme
【强制】3.7 String
规则：项目名_模块名_逻辑名称
示例：
project_module_login_tips
【强制】3.8 Shape
规则：项目名_模块名_shape[_不带#的小写背景色值][_形状][_corner角度]，形状参考“限定词缩写”中的“形状”表格
示例：
project_module_shape_ffffffff_rect_corner10，project_module_shape_299ee3_corner

【强制】3.9 为避免重复定义资源问题，资源文件顶部定义通用资源，通用资源包含：常用操作（确定、取消、重置等）、性别、单位（年、岁等）、网络（请求成功/失败、提交成功/失败等）、常用名词（拍照、相册等）、常用提示语（xxx不能为空）
【强制】3.10 优先搜索使用已存在资源，如需更改通用资源内容请先Find Usages，找涉及到该资源引用相关开发确认再修改
4.Android基本组件
【强制】4.1  Activity间的数据通信，对于数据量比较大的，避免使用 Intent + Parcelable的方式，可以考虑 EventBus 等替代方案，以免造成 TransactionTooLargeException
【强制】4.2  Activity 间通过隐式 Intent 的跳转，在发出 Intent 之前必须通过 resolveActivity检查，避免找不到合适的调用组件，造成 ActivityNotFoundException 的异常
【强制】4.3 避免在 Service#onStartCommand()/onBind()方法中执行耗时操作，如果确实有需求，应改用 IntentService 或采用其他异步机制完成
【强制】4.4 避免在 BroadcastReceiver#onReceive()中执行耗时操作，mo可以在子线程里做
【强制】4.5 避免使用隐式 Intent 广播敏感信息，信息可能被其他注册了对应 BroadcastReceiver 的 App 接收， 如果广播仅限于应用内，则可以使用LocalBroadcastManager#sendBroadcast()实现，避免敏感信息外泄和 Intent 拦截的风险
【建议】4.6 添加 Fragment 时 ， 确 保FragmentTransaction#commit() 在 Activity#onPostResume()或者FragmentActivity#onResumeFragments()内调用，也可在onCreate()中调用。 不要随意使用 FragmentTransaction#commitAllowingStateLoss()来代替，任何 commitAllowingStateLoss()的使用必须经过 code review，确保无负面影响
【强制】4.7 不要在 Activity#onDestroy()内执行释放资源的工作，例如一些工作线程的 销毁和停止，因为 onDestroy()执行的时机可能较晚。可根据实际需要，在 Activity#onPause()/onStop()中结合 isFinishing()的判断来执行
【强制】4.8 总是使用显式Intent启动或者绑定Service，且不要为服务声明IntentFilter， 保证应用的安全性。如果确实需要使用隐式调用，则可为 Service 提供 Intent Filter 并从 Intent 中排除相应的组件名称，但必须搭配使用 Intent#setPackage()方法设置 Intent 的指定包名，这样可以充分消除目标服务的不确定性
【建议】4.9 Service 需要以多线程来并发处理多个启动请求，建议使用 IntentService， 可避免各种复杂的设置
【强制】4.10 当前 Activity 的 onPause 方法执行结束后才会执行下一个 Activity 的 onCreate 方法，所以在 onPause 方法中不适合做耗时较长的工作，这会影响到页面之间的跳转效率
【建议】4.11 不要在 Android 的 Application 对象中缓存数据。基础组件之间的数据共享 请使用 Intent 等机制，也可使用 SharedPreferences 等数据持久化机制
【强制】4.12 使用 Toast 时，建议定义一个全局的 Toast 对象，这样可以避免连续显示 Toast 时不能取消上一次 Toast 消息的情况(如果你有连续弹出 Toast 的情况，避免使用 Toast.makeText（）
【强制】4.13 使用 Adapter 的时候，如果你使用了 ViewHolder 做缓存，在 getView()的 方法中无论这项 convertView 的每个子控件是否需要设置属性(比如某个 TextView 设置的文本可能为 null，某个按钮的背景色为透明，某控件的颜色为透明等)，都需 要为其显式设置属性(Textview 的文本为空也需要设置 setText("")，背景透明也需要 设置)，否则在滑动的过程中，因为 adapter item 复用的原因，会出现内容的显示错乱
【强制】4.14 Activity 或者 Fragment 中动态注册 BroadCastReceiver 时，registerReceiver() 和 unregisterReceiver()要成对出现
【强制】4.15 避免点击Home键回到桌面后，再次点击应用图标时出现启动界面，强制在应用入口Activity onCreate里做isTaskRoot判断
5.UI与布局
【强制】5.1 布局中不得不使用 ViewGroup 多重嵌套时，不要使用 LinearLayout 嵌套， 改用 RelativeLayout，可以有效降低嵌套数，嵌套越多measure次数越多，导致耗时
【强制】5.2 源文件统一采用 UTF-8 的形式进行编码
【强制】5.3 禁止在非 ui 线程进行 view 相关操作
【强制】5.4 禁止在设计布局时多次设置子 view 和父 view 中为同样的背景造成页面过度绘制，推荐将不需要显示的布局进行及时隐藏
【建议】5.5 灵活使用布局，推荐Merge、ViewStub 来优化布局，尽可能多的减少 UI 布局层级
【建议】5.6 尽量不要使用 AnimationDrawable，它在初始化的时候就将所有图片加载到内存中，特别占内存
【强制】5.7 不能使用 ScrollView 包裹 ListView/GridView/ExpandableListVIew;因为这样会把 ListView 的所有 Item 都加载到内存中，要消耗巨大的内存和 cpu 去绘制页面，确实需要使用嵌套，可采用NestedScrollView
【建议】5.8 Layout资源文件夹下分：activity、fragment、adapter、dialog等文件夹
6.进程、线程与消息通信
【建议】6.1 在 Application 的业务初始化代码加入进程判断，确保只在自己需要的进程 初始化。特别是后台进程减少不必要的业务初始化
【建议】6.2 新建线程时，必须通过线程池提供(AsyncTask 或者 ThreadPoolExecutor 或者其他形式自定义的线程池)，不建议在应用中自行显式创建线程
【强制】6.3 不要在非 UI 线程中初始化 ViewStub，否则会返回 null
【强制】6.4 ThreadPoolExecutor设置线程存活时间(setKeepAliveTime)，确保空闲时线程被释放
【建议】6.5 线程创建时设置线程名，以便查找问题时容易定位，个别强需求可做强制设置
7.文件与数据库
【强制】7.1 任何时候不要硬编码文件路径，请使用Android文件系统API访问
【强制】7.2 当使用外部存储时，必须检查外部存储的可用性
【强制】7.3 数据库 Cursor 必须确保使用完后关闭，以免内存泄漏
【建议】7.4 多线程操作写入数据库时，需要使用事务，以免出现同步问题
【强制】【Review】7.5 执行 SQL 语句时，应使用 SQLiteDatabase#insert()、update()、delete()， 不要使用 SQLiteDatabase#execSQL()（特殊情况需要review），以免 SQL 注入风险
【强制】7.6 如果 ContentProvider 管理的数据存储在 SQL 数据库中，应该避免将不受 信任的外部数据直接拼接在原始 SQL 语句中，可使用一个用于将 ? 作为可替换参 数的选择子句以及一个单独的选择参数数组，会避免 SQL 注入
【建议】7.7 Debug模式时建议开启严苛模式，方便定位文件写入耗时、资源泄露等问题
if (BuildConfig.DEBUG) {
      StrictMode.setThreadPolicy(new StrictMode.ThreadPolicy.Builder().detectAll().penaltyLog().build());
      StrictMode.setVmPolicy(new StrictMode.VmPolicy.Builder().detectAll().penaltyLog().build());
}
8.Bitmap、Drawable与动画
【强制】8.1 加载大图片或者一次性加载多张图片，应该在异步线程中进行。图片的加载，涉及到 IO 操作，以及 CPU 密集操作，很可能引起卡顿
【强制】8.2 在 ListView，ViewPager，RecyclerView，GirdView 等组件中使用图片时， 应做好图片的缓存，避免始终持有图片导致内存泄露，也避免重复创建图片，引起性能问题，统一使用Glide
【强制】8.3 png 图片使用 tinypng 或者类似工具压缩处理，减少包体积，统一使用webp格式（.9图特殊处理）
【建议】8.4 应根据实际展示需要，压缩图片，而不是直接显示原图。手机屏幕比较小，直接显示原图，并不会增加视觉上的收益，但是却会耗费大量宝贵的内存
【强制】8.5 使用完毕的图片，应该及时回收，释放宝贵的内存,使用结束，在 2.3.3 及以下需要调用 recycle()函数，在 2.3.3 以上 GC 会自动管理
【强制】8.6 在 Activity.onPause()或 Activity.onStop()回调中，及时调用clearAnimation()关闭当前 activity 正在执 行的的动画
【建议】8.7 使用 ARGB_565 代替 ARGB_8888，在不怎么降低视觉效果的前提下，减少内存占用
【建议】8.8 谨慎使用 gif 图片，注意限制单个gif 图片的大小
9.安全
【强制】9.1 App强制加上混淆，具体参考：Proguard手册
【强制】9.2 将android:allowbackup属性设置为 false(默认为true)，防止 adb backup 导出数据
【强制】9.3 Receiver/Provider 不能在毫无权限控制的情况下将android:export设置 为 true
【强制】9.4 敏感数据存储需要对数据进行加密
【强制】9.5 应用发布前确保android:debuggable属性设置为 false（默认为false）
【强制】9.6 密钥加密存储或者经过变形处理后用于加解密运算，切勿硬编码到代码中（定义在Property文件中）
【建议】9.7 使用 Android 的 AES/DES/DESede 加密算法时，建议不要使用默认的加密模式ECB，应显示指定使用 CBC 或 CFB 加密模式
【强制】9.8 AndroidAPP在HTTPS通信中，验证策略需要改成严格模式。Android APP 在 HTTPS 通信中，使用 ALLOW_ALL_HOSTNAME_VERIFIER，表示允许和 所有的 HOST 建立 SSL 通信，这会存在中间人攻击的风险，最终导致敏感信息可能会被劫持，以及其他形式的攻击
【建议】9.9 加密算法使用不安全的 Hash 算法(MD5/SHA-1)加密信息，存在被破解的风险，建议使用 SHA-256 等安全性更高的 Hash 算法
【强制】9.10 使用PendingIntent时，禁止使用空Intent与隐式Intent，会导致恶意用户劫持修改Intent内容
【强制】9.11 对安全要求较高App，可通过window.setFlag(LayoutParam.FLAG_SECURE)禁止使用截屏
【强制】9.12 涉及危险级别权限（与用户隐私相关权限）需要动态申请，配置文件中的静态申请必须去除
【强制】9.13 通过广播发送重要信息时，需做权限双向保护，如果权限是自定义的还需加上签名级别保护
10.库引用
【强制】10.1 使用标准第三方库引入方式，禁止对第三方库版本做单独管理，正方例子：implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:xxx”；反方例子：implementation rootProject.ext.dependencies["converter_gson”]
【强制】10.2 定期检测build.gradle中第三方库引用是否过期（如果是标准引入方式，可查看引用地址背景色是否变为黄色，且鼠标放上去Android Studio会提示存在新版本）
【强制】10.3 support库全部转为androidx（循序推进）
四、预测试流程
        【强制】1.1 Debug阶段增加静态代码检测工具Lint
等级
错误目录
错误类型
实例


1


Android
Android XML element is not allowed（错误的元素）
<scale xmlns:android="http://schemas.android.com/apk/res/android">
<scale
android:fromXScale="1.0"


Android Resources Validation（资源验证不过）
<item
  android:id="@+android:id/login_name"></item>
1
Android > Lint > Internationalization
Hardcoded text（硬编码）
<TextView
android:layout_width="100dp"
android:layout_height="100dp"
android:text="降价"/>







1








Android > Lint > Performance

Handler reference leaks（Handler要静态，否则可能内存泄露）
private Handler mHandler = new Handler()
{
@Override
public void handleMessage(Message msg)
{


Layout has too many views（View太多）
'order_detail_for_reserve_view.xml' has more than 80 views, bad for performance


Layout hierarchy is too deep（布局太深）
'activity_order_detail.xml' has more than 10 levels, bad for performance


Memory allocations within drawing code（避免在绘制或者解析布局(draw/layout)时分配对象）



Static Field Leaks（静态泄露）
public class BaseStatisticsActivity
{
static String mtitle;
static Context mContext;


Unused resources(无用的资源)



Useless parent layout（无用的父布局，有些布局没用就删掉）



Duplicated icons under different names(相同的资源不同的名称)
The following unrelated icon files have identical contents: lion_close.png, show_lion_close.png
2
Imports
Unused import（无用的导入包）

1
Probable bugs
这种错误的目录全都需要修改，防止程序crash

2
Verbose or redundant code constructs
Redundant type cast（冗余的类型转换）
holder.line = (View) convertView.findViewById(R.id.v_line_voucher);
2
XML
Unused XML schema declaration（未使用的导入）

        【强制】1.2 Debug阶段增加内存泄露分析器LeakCanary， 性能指标参考：APP性能指标
五、其他
1.Review
【强制】1.1 代码提交Git需要有其他成员review记录，模板：1.xxxx 2.xxxxx reviewed by xxx，reviewed by xxx需要单起一行展示，如果有结束某bug单，需要把bug单标题和单号也加上，如下示例：
1.bug-view-6345：已结束历史任务再次结束任务程序停止运行
2.解决推送失败问题
reviewed by xxx
2.Git
【强制】2.1 项目及Lib库开发需要做分支管理，具体标准参照：Git版本控制系统管理规范-分支管理
【强制】2.2 项目迭代及Lib库开发结束需要做封版，具体标准参照：Git版本控制系统管理规范-Tag封版
【强制】2.3 AS提交Git前勾选Reformat code、Rearrange code、Optimize imports
【强制】2.4 Lib库提交必须带有README文件，具体模板参照Lib库README模板
【强制】2.5 Apk归档需要包含apk文件和mapping.zip（包含mapping.txt，seeds.txt，usage.txt，dump.txt）
3.Maven
【强制】3.1 Maven正式发布包放置android_release目录下，测试发布包放置android_snapshots目录，开发测试发布包version后接“-SNAPSHOT”标识
【强制】3.2 Lib库责任人定期清理Maven无用库，删除（或修改）库必须提前告知相关人员，以便同事有足够时间去修改
【强制】3.3 Lib库命名统一使用“nl-”+功能形式
【强制】3.4 Lib库如包含多个子lib，需将子lib统一放入文件夹管理，通过扩展一级group来实现。如纳龙推送包含以下库：com.nl.library:nl-push-jiguang:xxx、com.nl.library:nl-push-websocket:xxx，应将group扩展一级，com.nl.library.nl-push:jiguang:xxx,com.nl.library.nl-push:websocket:xxx
【强制】3.5 Lib库初版本统一从1.0.0开始，后续版本视解决问题或模块来升版，具体升版原则参照Semver
4.Jenkins
【建议】4.1 Apk名称建议不要太长，以免Jenkins邮件插件发送附件至邮箱后，切割了部分附件名，导致安装不了Apk

