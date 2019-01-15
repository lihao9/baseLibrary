# baselibrary
个人项目使用基础库 借鉴参考 https://github.com/lihao9/AndroidUtilCode

#个人使用baselibrary库 参考：

##1.BaseActivity、BaseFragment基础Activity和Fragment类。封装功能如下： ButterKnife初始化 自定义顶部标题栏（左中右内容填充）封装 activity入栈、出栈（退出程序使用） 进度条封装 Toast显示封装 屏幕方向控制

##2.AlertDialog封装
- 2.1.初始化方法AlertDialogUtil(Activity activity, int resourceId)---初始化dialog的视图

- 2.2.setInitDialog(InitDialog initDialog):视图内控件的点击事件回调接口设置

- 2.3.init(int flag):初始化dialog的视图（视图控件寻找、点击事件设置），flag参数为控制在同一个页面内有多个不同的dialog显示时逻辑的处理。

- 2.4.dissmissDialog:隐藏dialog

##3.StatusBarUtil状态栏处理(沉寂式效果)

- 3.1.设置状态栏颜色--setColor(Activity activity, @ColorInt int color, @IntRange(from = 0, to = 255) int statusBarAlpha)：设置状态栏颜色，需要更改状态栏颜色的activity，状态栏的颜色，状态栏透明度。

- 3.2.setColorForSwipeBack(Activity activity, @ColorInt int color,@IntRange(from = 0, to = 255) int statusBarAlpha)：为滑动返回界面设置状态栏颜色

- 3.3.setColorForDrawerLayout(Activity activity, DrawerLayout drawerLayout, @ColorInt int color,@IntRange(from = 0, to = 255) int statusBarAlpha)：为DrawerLayout 布局设置状态栏变色

- 3.4.setTransparentForImageView(Activity activity, View needOffsetView)：为头部是 ImageView 的界面设置状态栏全透明，needOffsetView为需要向下偏移的 View

- 3.5.setTranslucentForImageView(Activity activity, @IntRange(from = 0, to = 255) int statusBarAlpha,View needOffsetView)：为头部是 ImageView 的界面设置状态栏透明

- 3.6.setTranslucentForImageViewInFragment(Activity activity, @IntRange(from = 0, to = 255) int statusBarAlpha,View needOffsetView)：为 fragment 头部是 ImageView 的设置状态栏透明

- 3.7.createStatusBarView(Activity activity, @ColorInt int color, int alpha)：生成一个和状态栏大小相同的半透明矩形条

- 3.8.getStatusBarHeight(Context context)：获取状态栏高度

- 3.9.calculateStatusColor(@ColorInt int color, int alpha)：根据颜色和透明度计算最终颜色值

##4.倒计时工具类CountDownTimerUtils（发送短信后的倒计时） 

倒计时工具类主要用在闪屏页进入主页面和获取验证码后倒计时等待，主要方法CountDownTimerUtils(Activity activity,Activity activity1,View view, int flag,long millisInFuture, long countDownInterval)：构造函数，activity是倒计时要显示界面；activity1是要跳转的页面；view是显示倒计时的控件；flag是倒计时类别（需要界面跳转、不需要跳转）；总时间；变动的间隔时间。

##5.文件相关工具FileUtil、FileUtil1

主要是对图片进行保存时用到，封装方法如下：还有一个为网上下载的文件相关工具类

- 5.1.createParentFile(String parentFilePath,String classFile)：根据父路径（一般项目名，不需要完整的路径）与文件类型创建文件

- 5.2.createImageFile(String parentFilePath,String classFile)：根据父路径与文件创建随机名字的图片文件

- 5.3createCustomFile(String parentFilePath,String classFile,String fileName)：根据父路径与文件类型以及文件名创建文件

##6.图片工具类BitmapUtil

图片工具类主要用于图片压缩、存储相关作用，主要方法如下：

- 6.1.Bitmap compressImage(Bitmap image,int size)：质量压缩方法---bitmap大小不变，保存的文件会变小适合图片上传。Bitmap要压缩的图片，size需要压缩至的大小（如果最总压缩参数仍然大于此数值则直接以最后一次压缩的结果为准）

- 6.2.Bitmap zoomImage(Bitmap bgimage，int size)：图片的缩放压缩方法，size压缩后的大小

- 6.3Bitmap fixedImage(Bitmap image,int wight,int height):固定宽高的压缩方式，wight图片保存的宽度，height图片保存的高度。

- 6.4saveBitmap(Bitmap bitmap,String parentPath,String classPath,String fileName)：保存图片，parentPath图片的父路径（一般为项目名称）；classPath：文件类型（image）;fileName图片名称。

##7.日志输出工具类LogUtil

日志输出都使用该类，封装了不同级别的日志输出，主要方法如下



- 7.1.boolean isDebuggable()：用于设置是否开启日志输出

- 7.2.getMethodNames(StackTraceElement[] sElements)：获取异常处的信息（类名、行号、方法）

- 7.3.createLog( String log )：创建log格式信息

- 7.4.e(String message)：错误日志输出

- 7.5.i(String message)：info日志输出

其他等级信息类似

##8.正则匹配工具类MatcherUtil

正则匹配目前有电话号码、姓名、6-12位的密码、银行卡匹配，具体方法如下：

- 8.1.Boolean isPhone(String value)：是否是电话号码,是则返回true

- 8.2.boolean isBankCard(String value):是否是银行卡，是则返回true

- 8.3.boolean isPassword(String value):是否是正确的密码，是则返回true

- 8.4.boolean isLegalName(String name):是否符合姓名规则，是则返回true

- 8.5.boolean isEmail(String value):是否符合邮箱规则，是则返回true

##2.9权限申请工具PermissionUtil

- boolean getExternalStoragePermissions(@NonNull Activity activity, int requestCode)：获取存储权限，内部会去申请权限。

- boolean getCameraPermissions(@NonNull Activity activity, int requestCode)：获取相机使用权限

- boolean getAudioPermissions(@NonNull Activity activity, int requestCode)：获取麦克风使用权限

- boolean getLocationPermissions(@NonNull Activity activity, int requestCode)：获取定位全下

- boolean getContactsPermissions(@NonNull Activity activity, int requestCode)：获取读取联系人的权限

- boolean getSendSMSPermissions(@NonNull Activity activity, int requestCode)：获取发送短信权限

- boolean getCallPhonePermissions(@NonNull Activity activity, int requestCode)：获取拨打电话的权限

- startApplicationDetailsSettings(@NonNull Activity activity, int requestCode)：进入对应app的设置界面（手动开启权限）

- onRequestPermissionsResult(int requestCode, @NonNull String[] permissions,@NonNull int[] grantResults, @NonNull OnRequestPermissionsResultCallbacks callBack) ：权限申请结果的回调


##2.10设备相关工具类PhoneInfoUtil
获取手机基本信息，目前方法如下：

- String getModel()：获取手机型号

- String getRom(Context context)：获取手机Rom（64G）

- String getRam()：获取手机Ram（4G）

##2.11屏幕相关ScreenUtil
主要是一些与屏幕操作相关的方法的封装，具体方法如下：

- int getScreenWidth()、getScreenHeight()：获取屏幕宽和高

- setFullScreen(@NonNull final Activity activity)、setNonFullScreen(@NonNull final Activity activity)：设置全屏和非全屏

- setLandscape(@NonNull final Activity activity)、setPortrait(@NonNull final Activity activity)：设置横屏、竖屏

- int dp2px(final float dpValue)、int px2dp(final float pxValue)、int sp2px(final float spValue)、int px2sp(final float pxValue)：dp、sp与px相互转换

##2.12文件存储工具类SharedPreferencesUtil
存取用户信息工具类，主要方法如下：

- setParam(Context context , String key, Object object)：存储信息，上下文、存储的key，存储的value

- Object getParam(Context context , String key, Object defaultObject)：根据key的值获取存储的对应值

- clearAll(Context context)：清除当前文件下所有的数据

- clear(Context context,String key)：清除指定数据，根据key，清除对应的值

##2.13富文本工具类SpannableUtil
用于富文本显示的工具类（本类采用链式调用），主要方法如下：

- setColor(int start, int end, String color)：设置文本部分字体的颜色，带颜色文字开始位置、结束位置、文字颜色

- setSize(float size,int start,int end)：设置文字大小

- setOnClick(ClickableSpan clickableSpan,int start,int end)：为部分文字设置点击事件，点击事件处理类、有点击事件文字的开始位置、结束位置

##2.14时间转化工具类TimeUtil
主要封装了时间、毫秒数、字符之间的转换，主要方法如下：

- String ms2Date(long _ms)：毫秒数转时间格式（可以添加转换格式）

- long Date2ms(String _data)：时间格式转时间戳

- String dateToString(Date date, String format)：时间格式转字符格式，format字符格式（yyyy-MM-dd）

- String formatChineseDate(String strDate)：将时间格式转化为中文字符（2000年10月01日）

- Date getEndWeekDay(Date date)：获得某一日期对应的星期五是哪一天

- Date relativeDate(Date date, int days)：计算某一日期之前或之后的日期

- Date toDate(String strDate, String strFormat)：字符串转时间，strFormat时间格式

- String getDate(int num)：得到当前日期前后n天日期

##2.15二维码生成工具类QRCodeUtil
主要作用是根据特定的字符生成特定的二维码图片，主要方法如下：

    createQRCodeBitmap(@Nullable String content, int size,@Nullable String character_set, 
    @Nullable String error_correction, @Nullable String margin,
    @ColorInt int color_black, @ColorInt int color_white, @Nullable Bitmap targetBitmap,
    @Nullable Bitmap logoBitmap, float logoPercent)
    根据参数生成特定的二维码：
    content：二维码内容
    size：二维码宽高
    character_set：字符集/字符转码格式，传null时,默认使用 "ISO-8859-1
    error_correction：容错级别，传null时,zxing源码默认使用 "L"
    margin：空白边距 (可修改,要求:整型且>=0),默认值是”4”
    color_black：黑色色块的自定义颜色值
    color_white：白色色块的自定义颜色值
    targetBitmap：目标图片 (如果targetBitmap != null, 黑色色块将会被该图片像素色值替代)
    logoBitmap：logo小图片
    logoPercent：logo小图片在二维码图片中的占比大小,范围[0F,1F],超出范围->默认使用0.2F。

##2.16常量类Constant

主要存储一些全局都可用的常量数据


