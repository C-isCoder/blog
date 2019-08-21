+++
author = "Xiaodan.C"
categories = ["Android"]
date = "2019-08-20"
description = "Android dev"
featured = "pic01.jpg"
featuredalt = "Pic 1"
featuredpath = "date"
linktitle = ""
title = "Android 开发手册"
type = "post"
+++

## 工程


### 结构

* 整体项目0依赖 model ，单一模块工程

![](/img/2019/07/1.png)
![](/img/2019/07/2.png)

1. 包划分：按照项目功能模块划分，模块下根据功能的多少，考虑是否细分包。
2. 配置文件，由之前的单一 Gradle 文件，拆分为 **thrid.gradle**（第三方依赖）、**thrid-key.gradle**（第三方依赖的key）、**version.gradle**（项目管理）。**Jenkinsfile**（CI流程文件）


### 架构组织（MVP）

* 每个页面由3个文件 xxxActivity\Fragment，xxxContract，xxxPresenter 

![](/img/2019/07/3.png)


## 规范


### 包命名

* 功能名，对应的::英文单词，全小写:: 
* eg：`com.baichang.consumer.active`


### Activity、Fragment、Service、类名

* 功能名，对应的::英文单词，首字母大写+Activity\Fragment\Service:: 
* eg：`MessageActivity、MessageFragment、MessageService`


### XML资源文件


#### 颜色

* ::类型_名称+色值后两位(大写)::
* eg：`font_color_blackBD`  -> `#FFBDBDBD`


#### 文字

1. 普通提示类型的文字描述：::tips_英文描述::

eg：`tips_please_input_name` -> `请输入您的名字`

```xml
<string name="tips_please_input_name">请输入您的名字</string>
```

2.  成功/失败类型的文字描述： ::tips_英文描述_success\failed::

eg：`tips_submit_success` -> `提交成功`

```xml
<string name="tips_submit_success">提交成功</string>
<string name="tips_submit_failed">提交失败</string>
```

3. 带有格式化类型的文字描述：::format_英文描述::

eg：`format_card_invalid` -> `失效日期：%s`

```xml
<string name="format_card_invalid">失效日期：%s</string>
```

4. 普通类型的文字描述：::英文单词_英文单词::

eg：`collar_center` -> `领券中心`

```xml
<string name="collar_center">领券中心</string>
```


#### AndroidMainfest.xml

* 所有的 Activity、Service 必须注释中文模块名

```xml
/<!-- 意见反馈 -->/
<activity android:name=".mine.feedback.FeedbackActivity"/>
/<!-- 服务协议 -->/
<activity android:name=".login.ServiceProtocolActivity"/>
/<!-- 活动中心 -->/
<activity android:name=".active.ActiveActivity"/>
/<!-- 省市区数据服务 -->/
<service
    android:name=".service.ChinaTownIntentService"
    android:exported="false">
```


#### 布局文件

* Activity\Fragment 布局文件 ::Activity\Fragment_模块\功能英文名全小写::

eg：`activity\fragment_message`

* ListItem布局文件::item_模块\功能英文名全小写::
  
eg：`item_message`

* 引入布局文件::include_模块\功能英文名全小写::
  
eg：`include_message_header`

* Dialog布局文件::dialog_模块\功能英文名全小写::
  
eg：`dialog_message`

* PopupWindow布局文件::pop_模块\功能英文名全小写::
  
eg：`pop_message`


#### Drawable资源文件 

> _**颜色、圆角只在有多个相同功能，不同样式的情况下使用**_ 

* 按钮类型的 drawable ::button_功能\模块英文名全小写_颜色_圆角:: 

eg：`button_back_white_10`

* Shape类型的 drawable ::shape_功能\模块英文名全小写_颜色_圆角::
  
eg：`shape_address`

* Selector类型的 drawable ::selector_功能\模块英文名全小写_颜色_圆角::
  
eg：`selector_address`

* 其他的类型以控件名字为前缀，例如 **checkbox**、**radio**

eg：`radio_sex_man checkbox_eye`

* 项目首页下边4个Tab按钮单独命名为::tab_模块英文名小写::

eg：`tab_home`


### 代码

#### 常量、变量命名

> _**优先 val 常量命名，除非要求可变，才会用 var**_  

1. 全局变量名，关键字::**var**::，遵循::驼峰命名::规则，尽量简洁明了，不超过2个单词。

eg：`private var nowPage = 1`

2. 全局常量名，关键字::**val**::，遵循::驼峰命名::规则，尽量简洁明了，不超过2个单词。

eg：`private val preferences = view.getPreferences()`

3. 局部变量，尽可能使用::**val**::，遵循::驼峰命名::规则，尽量简洁明了。不超过2个单词。

eg：`val phone = view.getNumber()`

4. 静态全局常量，kotlin 中，需要在半生对象中声明静态全局常量，::大写英文字母_链接::
   
```java
companion object {
  const val REFRESH_CODE = 10010
}
```

访问：`类名.REFRESH_CODE`

5. Bool类型声明，关键字::is、has、can+英文::，遵循::驼峰命名::规则，尽量简洁明了，不超过2个单词。
   
eg：`var isRefresh = true、var hasCallPermission = true、var canClose = false`


#### 控件的命名

> _**同一个布局文件中，名称唯一**_  

1. 常用控件，遵循::驼峰命名，简称+功能::规则，尽量简洁，不超过2个单词。（对于刷新控件统一命名为`progress`）

eg：`tvName,ivAvatar,llPhone,rlLayout,rvList,cbSex,rbMan,btnSubmit`

2. 特殊命名，在 RelativeLayout 布局中，仅仅作为布局的相对位置描述的命名（不参与代码的逻辑），采用::_单词::的方式，长度为1个英文单词。

eg：`_title,_card`


#### 类、方法命名

* 遵循::驼峰命名，动词+名字\形容词::规则，类名::首字母大写::，尽量简洁的表达出，方法\类的功能\作用，不超过3个单子。

```coffee
fun showMessage(msg: String)
fun showMessage(msgId: Int)
fun showProgress()
fun hideProgress()
fun setIngots(number: String)
fun setAnnouncement(list: List<String>)
fun getPreferences(): SharedPreferences
fun startProgress(data: ActiveData)
fun setEmptyStatus(isShow: Boolean)
``` 

* 方法参数遵循::驼峰命名，动词+名字\形容词::规则，尽可能简洁，不超过2个单词。
* 方法、跳转避免对象的传递。
* 接口 Api 命名遵循::驼峰命名，动词+名字\形容词::规则，每个接口上方必须注释接口中文名称，尽量简洁。

```java
// 检查更新
@POST("app/checkEdition")
fun upgrade(@Body map: Map<String, String>): Observable<UpgradeData>

// 获取验证码
@POST("app/sendCode")
fun getCode(@Body map: Map<String, String>): Observable<Boolean>

// 验证码校验
@POST("app/checkPerfect")
fun checkCode(@Body map: Map<String, String>): Observable<Int>

// 登录
@POST("app/loginDirect")
fun login(@Body map: Map<String, String>): Observable<LoginData>
```


#### 代码书写

1. 方法名称，尽可能的表现出方法本身的作用，传参个数不超过3个，如果超出，拆分多个方法实现。
2. 尽可能保证代码一行展示，有利于阅读。
![](/img/2019/07/4.png)
3. 方法中 if else 嵌套不超过3层，try 捕获的情况不超过4层。
4. Activity/Fragment中，除了在 onCreate 方法中初始化布局以外，不得出现非 override 修饰的方法出现，广播接收的回调例外。
5. 本地缓存、页面跳转，存储的 Key 集中存放，命名遵循静态全局常量。
   
```java
// 缓存
object Cache {
  const val USER_AVATAR = "user_avatar"
  const val USER_NAME = "user_name"
  const val USER_SEX = "user_sex"
  const val USER_ID = "user_id"
}
//  传值/广播
object Constants {
  const val INTENT_MESSAGE_DATA = "intent_message_data"
  const val INTENT_QR_CODE_RESULT = "intent_qr_code_result"
  const val INTENT_BRANDS_ID = "intent_position" 
  const val BROADCAST_PUSH_MESSAGE = "push_message"
  const val BROADCAST_REFRESH_MONEY = "broadcast_money"
  const val BROADCAST_UPDATE_MONEY = "broadcast_update_money"
  const val BROADCAST_WX_SUCCESS = "broadcast_wx_success"
}
```

1. 事件通知，避免使用 EventBus 实现，改用原生的本地广播。
2. 网络请求成功回调后对控件的操作，要考虑到页面销毁的情况，对用到的控件用::?::实行空安全。

```coffee
override fun showProgress() {
  refresh?.show()
}

override fun hideProgress() {
  refresh?.hide()
}
```

3. 第三方依赖做好版本管理

```java
ext {
  retrofit_version = *'2.3.0'*
converter_gson_version = *'2.3.0'*
adapter_rxjava2_version = *'2.3.0'*
rxandroid_version = *'2.0.1'*
constraint_layout_version = *'1.1.0'*
support_version = *'27.1.1'*
circleimageview_version = *'2.2.0'*
swipedelmenulayout_version = *'V1.3.0'*
glide_version = *'4.4.0'*
anko_version = *'0.10.4'*
gradle_version = *'3.0.1'*
bga_qrcode_zxing_version = *'1.2.1'*
jpush_version = *'3.1.1'*
jcore_version = *'1.1.9'*
janalytics_version = *'1.1.1'*
mpchart_version = *'v3.0.3'*
datetimepicker_version = *'2.0.0'*
ktx_version = *'0.3'*
gallery_pager_version = *'0.0.5'*
wechat_sdk_version = *'5.1.4'*
marquee_view = *'1.3.3'*
}
dependencies {
  implementation fileTree(*include*: [*'*.jar'*], *dir*: *'libs'*)
  implementation *"androidx.core:core-ktx:*$ktx_version*"*
implementation *"com.android.support:design:*$support_version*"*
implementation *"com.android.support:support-v4:*$support_version*"*
implementation *'com.android.support:support-v4:27.1.1'*
implementation *"com.android.support:appcompat-v7:*$support_version*"*
implementation *"com.android.support:support-vector-drawable:*$support_version*"*
implementation *"com.squareup.retrofit2:retrofit:*$retrofit_version*"*
implementation *"com.squareup.retrofit2:converter-gson:*$converter_gson_version*"*
implementation *"com.squareup.retrofit2:adapter-rxjava2:*$adapter_rxjava2_version*"*
implementation *"io.reactivex.rxjava2:rxandroid:*$rxandroid_version*"*
implementation *"de.hdodenhof:circleimageview:*$circleimageview_version*"*
implementation *"com.android.support:cardview-v7:*$support_version*"*
implementation *"com.android.support.constraint:constraint-layout:*$constraint_layout_version*"*
implementation *"org.jetbrains.anko:anko:*$anko_version*"*
implementation *"cn.jiguang.sdk:jcore:*$jcore_version*"*
implementation *"cn.jiguang.sdk:jpush:*$jpush_version*"*
implementation *"cn.jiguang.sdk:janalytics:*$janalytics_version*"*
implementation(*"com.github.bumptech.glide:glide:*$glide_version*"*) {
    exclude *group*: *"com.android.support"*
}
  implementation *"cn.bingoogolapple:bga-qrcode-zxing:*$bga_qrcode_zxing_version*"*
implementation *"com.github.RainbleNi:GalleryViewPager:*$gallery_pager_version*"*
implementation *"com.tencent.mm.opensdk:wechat-sdk-android-without-mta:*$wechat_sdk_version*"*
implementation *"com.sunfusheng:marqueeview:*$marquee_view*"*
}
```

4. 项目中不能出现硬编码，所有文字相关的要写到，strings.xml文件中。
5.  接口方法中，有未实现的方法要注释  `//ignore`  进行忽略。
6.  接口返回的数据对象中有类似于 type 值对应不同状态的，必须对字段进行注释。

```java
data class ActiveData(
  var activeDegree: Int,      //用户参与活动限制次数
  var activeStartTime: String,//开始时间
  var activeStatus: Int,      //活动状态 0未开始 1倒计时 2进行中 3结束 ,
  val id: Int,                //id
  var needMoney: Int,         //需要的money
  var percent: Int,           //剩余百分比
  var prizeName: String,      //奖品的名称
  var prizePicture: String,   //奖品的图片key
  var remainder: Int,         //倒计时毫秒数
  var remark: String,         //备注
  var remarkNote: String      //活动描述
)
```


## MVP事例

> Activity  

* onCreated 中初始化控件

```java
class InviteActivity : CommonActivity(), InviteContract.View {

  override lateinit var presenter: InviteContract.Presenter

  override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_invite_code)
    InvitePresenter(this)
    btnShare.onClick { presenter.share() }
    iInvite.onClick { presenter.share() }
    tvCode.onClick { presenter.copy() }
    tvCode.onLongClick { presenter.copy() }
    JAnalyticsInterface.onPageStart(this, getString(R.string.j_invite))
  }

  override fun getClipboard(): ClipboardManager =
      getSystemService(Context.CLIPBOARD_SERVICE) as ClipboardManager

  override fun onStart() {
    super.onStart()
    presenter.start()
  }

  override fun showProgress() {
    progress?.show()
  }

  override fun hideProgress() {
    progress?.hide()
  }

  override fun showMessage(msg: String) {
    toast(msg)
  }

  override fun showMessage(msgRes: Int) {
    toast(msgRes)
  }

  override fun setCode(code: String) {
    tvCode?.text = code
  }

  override fun setQrCode(qr: Bitmap) {
    ivQrCode.setImageBitmap(qr)
  }

  override fun getQrContent(): String =
      defaultSharedPreferences.getString(Cache.USER_ADDRESS_ID, "")

  override fun dip(dp: Int): Int = getActivity().dip(dp)

  override fun getUserId(): String = defaultSharedPreferences.getString(Cache.USER_ID, "")

  override fun getContext(): Context = this

  override fun getManager(): FragmentManager = supportFragmentManager

  override fun onDestroy() {
    super.onDestroy()
    JAnalyticsInterface.onPageEnd(this, getString(R.string.j_invite))
  }
}
```

> Contract  

* 契约接口，约束Activity和Present交互规则

```java
interface InviteContract {
  interface View : CommonView<Presenter> {
    fun showProgress()
    fun hideProgress()
    fun showMessage(msg: String)
    fun showMessage(msgRes: Int)
    fun setCode(code: String)
    fun getResources(): Resources
    fun getContext(): Context
    fun dip(dp: Int): Int
    fun getQrContent(): String
    fun setQrCode(qr: Bitmap)
    fun getUserId(): String
    fun getManager(): FragmentManager
    fun getClipboard():ClipboardManager
  }

  interface Presenter : CommonPresenter {
    fun share()
    fun copy()
  }
}
```

> Presenter  

* 执行网络请求，耗时操作的地方::Persenter 中不能出现任何控件::

```java
class InvitePresenter(private val view: InviteContract.View) : InviteContract.Presenter {

  private var miniTitle: String? = null
  private var webTitle: String? = null
  private var description: String? = null
  private var miniId: String? = null
  private var webPageUrl: String? = null
  private var path: String? = null
  private var content: String? = null
  private var webUrl: String? = null
  private var inviteCode: String? = null

  init {
    view.presenter = this
  }

  override fun start() {
    HttpFactory.getInstance()
        .getInviteCode()
        .subscribeOn(Schedulers.newThread())
        .map {
          it.qrCode = QRCodeEncoder.syncEncodeQRCode(it.downloadLink, view.dip(130))
          return@map it
        }
        .observeOn(AndroidSchedulers.mainThread())
        .doOnSubscribe { view.showProgress() }
        .doOnTerminate { view.hideProgress() }
        .subscribe({ invite ->
          content = invite.shareContent
          inviteCode = invite.userCode
          view.setCode(invite.userCode)
          view.setQrCode(invite.qrCode)
        }, { view.showMessage(it.message!!) })
    HttpFactory.getInstance()
        .miniProgram()
        .compose(HttpFactory.schedulers())
        .subscribe({
          miniTitle = it.title
          description = it.description
          miniId = it.miniId
          webPageUrl = it.webpageUrl
          path = it.path
        }, { view.showMessage(it.message!!) })
    HttpFactory.getInstance()
        .webProgram()
        .compose(HttpFactory.schedulers())
        .subscribe({
          webTitle = it.title
          webUrl = it.pageUrl
        }, { view.showMessage(it.message!!) })
  }

  private val THUMB_WIDTH = 400
  private val THUMB_HEIGHT = 320
  private val THUMB_WEB = 200

  override fun share() {
    ShareUtil.show(view.getContext()) { type ->
      val api = WXAPIFactory.createWXAPI(view.getContext(), Constants.WX_APP_ID)
      when (type) {
        ShareUtil.WECHAT -> {
          val miniProgramObj = WXMiniProgramObject()
          webPageUrl?.let {
            miniProgramObj.webpageUrl = it
          }                                  // 兼容低版本的网页链接
          miniProgramObj.miniprogramType =
              WXMiniProgramObject.MINIPTOGRAM_TYPE_RELEASE       // 正式版:0，测试版:1，体验版:2
          miniId?.let {
            miniProgramObj.userName = it
          }                                        // 小程序原始id
          path?.let {
            miniProgramObj.path = it
          }                                              //小程序页面路径
          val msg = WXMediaMessage(miniProgramObj)
          miniTitle?.let {
            msg.title = it
          }                                                   // 小程序消息title
          description?.let {
            msg.description = it
          }                                           // 小程序消息desc
          val bmp = BitmapFactory.decodeResource(view.getResources(), R.mipmap.mini_card)
          val thumbBmp = Bitmap.createScaledBitmap(bmp, THUMB_WIDTH, THUMB_HEIGHT, true)
          bmp.recycle()
          msg.thumbData = Util.bmpToByteArray(thumbBmp, true)
          val req = SendMessageToWX.Req()
          req.transaction = "webpage${System.currentTimeMillis()}"
          req.message = msg
          req.scene =
              SendMessageToWX.Req.WXSceneSession                                        // 目前支持会话
          api.sendReq(req)
        }
        ShareUtil.CIRCLE -> {
          val webPageObj = WXWebpageObject()
          webUrl?.let { webPageObj.webpageUrl = it }
          val msg = WXMediaMessage(webPageObj)
          webTitle?.let { msg.title = it }
          msg.description = view.getResources()
              .getString(R.string.app_name)
          val bmp = BitmapFactory.decodeResource(view.getResources(), R.mipmap.icon_web)
          val thumbBmp = Bitmap.createScaledBitmap(bmp, THUMB_WEB, THUMB_WEB, true)
          bmp.recycle()
          msg.thumbData = Util.bmpToByteArray(thumbBmp, true)
          val req = SendMessageToWX.Req()
          req.transaction = "webpage${System.currentTimeMillis()}"
          req.message = msg
          req.scene = SendMessageToWX.Req.WXSceneTimeline
          api.sendReq(req)
        }
      }
    }
  }

  override fun copy() {
    inviteCode?.let {
      val clipboardManager = view.getClipboard()
      val appName = view.getResources()
          .getString(R.string.app_name)
      val clipData = ClipData.newPlainText(appName, inviteCode)
      clipboardManager.primaryClip = clipData
      view.showMessage(R.string.tips_invite_clip)
    }
  }

}
```


---
EOF