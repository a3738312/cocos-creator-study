# cocos-creator-study

资源文件(图片,预制体等)名称不要有特殊符号和中文,可能会有问题

ccc需要动态加载的在resources图片的图集，不要使用自动图集，否则会每个图片都生成一个json文件(没卵用)

ccc的editbox默认值为空的情况下，在第一次打开的时候设置内容会导致实际显示文字很小，需要手动重新设置fontSize

ccc的editbox就算是节点的active设置成false也会有效，且对于不同机型 enabled=false 可能会无效

ccc的editbox的在IOS上开启Stay On Top可能会导致点击无反应

ccc搭建安卓原生环境的时候要注意：ccc安装目录和sdk、ndk、ant的路径都不能有中文和空格

*ccc编译安卓原生的时候报错  
>Execution failed for task ':libcocos2dx:verifyReleaseResources'.  
>> com.android.ide.common.process.ProcessException: Failed to execute aapt  
可能是因为项目路径太深
