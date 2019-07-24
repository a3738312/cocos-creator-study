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



#原生
通过使用PowerManager里面的WakeLock可以使游戏不息屏

        private static PowerManager.WakeLock wakeLock;

        PowerManager _powerMgr = (PowerManager) getSystemService(Context.POWER_SERVICE);
        wakeLock = _powerMgr.newWakeLock(PowerManager.PARTIAL_WAKE_LOCK,TAG);
        wakeLock.acquire();
        
需要在AndroidManifest.xml添加权限

    <uses-permission android:name="android.permission.WAKE_LOCK" />
