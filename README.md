# cocos-creator-study

* 资源文件(图片,预制体等)名称不要有特殊符号和中文,可能会有问题  
* ccc需要动态加载的在resources图片的图集，不要使用自动图集，否则会每个图片都生成一个json文件(没卵用)  
* ccc的editbox默认值为空的情况下，在第一次打开的时候设置内容会导致实际显示文字很小，需要手动重新设置fontSize  
* ccc的editbox就算是节点的active设置成false也会有效，且对于不同机型 enabled=false 可能会无效  
* ccc的editbox的在IOS上开启Stay On Top可能会导致点击无反应  
* ccc搭建安卓原生环境的时候要注意：ccc安装目录和sdk、ndk、ant的路径都不能有中文和空格  
* ccc编译安卓原生的时候报错可能是因为项目路径太深  
> fatal error: opening dependency file 项目所在路径/hello/test/build/jsb-link/frameworks/runtime-src/proj.android-studio/app/build/intermediates/ndkBuild/release/obj/local/armeabi-v7a/objs/cocos2dx_static/scripting/js-bindings/jswrapper/v8/debugger/inspector_socket_server.o.d: No such file or directory  ··
* ccc调用java代码，java方法需要写静态，在调用jsb.reflection.callStaticMethod(类完整路径,方法名,方法签名,参数...);的时候  
* 方法签名必须和被调用方法保持一致，比如 ()V 表示没有参数也没有返回值，(I)V有int类型参数没有返回值 (I)I有int参数也有int返回值;没有对应会找不到方法  
* 特别注意String的方法签名 Ljava/lang/String; 后面的分号一定要加上去
* cccjava调用js代码，需要js代码是全局可用的:  
window.login();//js  
window['login']=()=>{}



# 原生

* 通过使用PowerManager里面的WakeLock可以使游戏不息屏
* https://blog.csdn.net/qq_32115439/article/details/80169222
* 接入一些需要设置某些值的SDK，要判断SDK和游戏都初始化完毕了再做后面的事情
* Google play servers 接入的时候要注意创建OAth2.0客户端，一个调试客户端，一个正式客户端
* 安卓Facebook分享需要base64图片或bitmap，可以在JS里处理图片(截图、拼图等)然后调用jsb.saveImageData()保存在本地，安卓根据路径读取图片直接以bitmap传入即可(会比较块)

# QQ小游戏
* 远程加载资源有不支持的文件格式，下载不支持的格式会报错 Download Fielded
* ccc在QQ小游戏里获取环境是安卓，要加判断
* ccc发布QQ小游戏流程：发布微信小游戏，用VS Code打开微信小游戏文件夹，全局搜索;wx.'替换成'qq.'；saveFile前需改成fs(和微信不一样)
