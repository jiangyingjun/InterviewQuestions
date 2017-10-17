# Android

---
### 单选题

1. WebView中可以用来处理js中警示，确认等对话框的是（C）
- [ ] A.WebSettings  
- [ ] B.WebViewClient  
- [x] C.WebChromeClient  
- [ ] D.WebViewChrome

2. 假设assets目录下有文件结构html/hello.html,用loadUrl()方法将该网页加载至webView时,需传入的参数是（B）
- [ ] A.file:///asset/html/hello.html
- [x] B.file:///android_asset/html/hello.html
- [ ] C.file:///androidasset/hello.html
- [ ] D.file:///assets/html/hello.html

3. 下列不属于补间动画相关类的是(B)
- [ ] A.TranslateAnimation    
- [x] B.FrameAnimation
- [ ] C.RotateAnimation
- [ ] D.AlphaAnimation

4. Android中网络互连中需要获取状态码，根据状态码来判断请求是否已经完成，下列状态码表示请求完成的是(D)
- [ ] A.100    
- [ ] B.202
- [ ] C.404
- [x] D.200

5. 关于ImageSwitcher说法错误的是（B）
- [ ] A.ImageSwitcher里可以通过Alpha设定转换时候的透明位
- [x] B.在使用一个ImageSwitcher之前，不一定要调用setFactory方法
- [ ] C.setInAnimation是设置资源被读入到这个ImageSwitcher的时候动画效果
- [ ] D.setOutAnimation是资源文件从这个ImageSwitcher里消失的时候要实现的动画效果

6. 建立蓝牙连接时通过（D）方法来获取BluetoothAdapter对象
- [ ] A.BluetoothAdapter.getBluetoothAdapterAdapter()
- [ ] B.BluetoothAdapter.adapter=new BluetoothAdapter();
- [ ] C.BluetoothAdapter.BluetoothAdapterAdapter();
- [x] D.BluetoothAdapter.getDefaultAdapter()

7. 关于Handler的说法不正确的是(A)
- [x] A.它实现不同进程间通信的一种机制
- [ ] B.它避免了在新线程中刷新UI的操作
- [ ] C.它采用队列的方式来存储Message
- [ ] D.它实现不同线程间通信的一种机制

8. Vector和ArrayList的主要区别是（B）：
- [ ] A.ArrayList内部基于链表，而Vector是基于数组的
- [x] B.Vector的大部分方法做了同步，而ArrayList没有同步
- [ ] C.Vector是可串行化的，而ArrayList不是
- [ ] D.Vector实现了RandomAccess，而ArrayList没有

9. 下列属于SAX解析xml文件的优点的是（B）
- [ ] A.将整个文档输在内存中，便于操作，支持删除，修改，重新排列等多种功能
- [x] B.不用事先调入整个文档，占用资源少
- [ ] C.整个文档调入内存，浪费时间和空间
- [ ] D.不是长久驻留在内存，数据不是持久的，事件过后，若没有保存数据，数据就会消失

10.String a1="abc"; String a2="abc"; String a3="abcd"; 总共创建(A)个String对象。
- [x] A.2
- [ ] B.3  
- [ ] C.5  
- [ ] D.6

### 多选题
1. 在添加第一个appwidget窗口小部件时，会执行的方法是（ABD）
- [x] A.onReceive
- [x] B.onEnabled
- [ ] C.onDisabled
- [x] D.onUpdate

2. 下列属于SOAP优点的是（ABCD）
- [x] A,SOAP与编程语言无关。SOAP可以使用任何语言来完成
- [x] B,SOAP是完全和厂商无关。
- [x] C,SOAP与平台无关
- [x] D,SOAP是简单的，可扩展的

3. 下列属于SAX解析XML需要用到的类和接口是（BCD）
- [ ] A.DocumentBuilder
- [x] B.SAXParser
- [x] C.DefaultHandler
- [x] D.SAXParserFactory

4. 在使用蓝牙必须获取的权限是（AD）
- [x] A.<uses-permission.android:name="android.permission.BLUETOOTH"/>
- [ ] B.<uses-permission.android:name="android.permission.INTERNET"/>
- [ ] C.<uses-permission.android:name="android.permission.BIND_BLUETOOTH"/>
- [x] D.<uses-permission.android:name="android.permission.BLUETOOTH_ADMIN"/>

5. Chronometer类的重要方法（ABC）
- [x] A.start
- [x] B.stop
- [x] C.setBase
- [ ] D.destory

---


### 问答题

#### 1. oom是什么?如何避免？
当程序需要申请一段“大”内存，但是虚拟机没有办法及时的给到，即使做了GC操作以后这就会抛出OutOfMemoryException也就是OOM避免：
###### 1)减少内存对象的占用
I.ArrayMap/SparseArray代替hashmap  
II.避免在android里面使用Enum  
III.减少bitmap的内存占用   
IV.减少资源图片的大小，过大的图片可以考虑分段加载内存对象的重复利用  
###### 2)大多数对象的复用，都是利用对象池的技术。
I.listview/gridview/recycleview.contentview的复用  
II.inBitmap属性对于内存对象的复用这个方法在某些条件下非常有用，比如要加载上千张图片的时候。  
III.避免在ondraw方法里面new对象  
IV.StringBuilder代替+
#### 2. SurfaceView&View的区别
view的更新必须在UIthread中进surfaceview会单独有一个线程做ui的更新。surfaceview支持openGL绘制。

#### 3.什么时候会发生内存泄露？内存泄露的根本原因?
长生命周期的对象持有短生命周期的对象。短周期对象就无法及时释放。  
I.静态集合类引起内存泄露  

II.remove方法无法删除set集Objects.hash(firstName,lastName); 

III.observer我们在使用监听器的时候，往往是addxxxlistener，但是当我们不需要的时候，忘记removexxxlistener，就容易内存leak。 

IV.各种数据链接没有关闭，数据库contentprovider，io，sokect等。cursor 

V.内部类：java中的内部类（匿名内部类），会持有宿主类的强引用this。  
所以如果是new Thread这种，后台线程的操作，当线程没有执行结束时，activity不会被回收。  
Context的引用，当TextView等等都会持有上下文的引用。如果有static.drawable，就会导致该内存无法释放。  

VI.单例单例是一个全局的静态对象，当持有某个复制的类A是，A无法被释放，内存leak。

#### 4.横竖屏切换时Activity的生命周期
切换时的生命周期跟清单文件里的配置有关系。
不设置Activity的android:configChanges时，切屏会重新调用各个生命周期默认首先销毁当前activity,然后重新加载。


---
### 面试题
2017/10/12   
#### 一 Android序列化有几种方式，那个性能好，好在哪里？  
答：1、Serizalizable 2、Parcelabe  

Serizalizable的作用是为了保存对象的属性到本地文件，数据库，网络流等方便数据传输。也可以用于程序内数据传输。
而Android 的Parcelable设计初衷就是为了解决Serializable效率慢，在内存中开销大的问题。为了在程序内不同组件以及不同的android程序间高效传输数据而设计的。这些数据仅在内存中，Parcelabe是通过Ibinder通信的消息载体 
