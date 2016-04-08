

本篇主要讲述了，

* 开发环境的安装(Java JDK以及Android Studio)
* Android Studio工程的Hello World
* Android Studio的项目结构
* ImageView和TextView的属性
* RelativeLayout的用法

在实现生日卡片应用的时候，我学到Android Studio的一些内容。

![Android Studio](http://7xljei.com1.z0.glb.clouddn.com/tree.png)

在Android Studio的xml文件的design页卡上，右上侧显示了布局控件的树形层级，下面是选中的控件的树形，右键可以查看属性的意思。快捷键是ctrl+shift+空格。

![code](http://7xljei.com1.z0.glb.clouddn.com/propertyofdesign.png)

在代码页卡中，按住上述的快捷键，也可以显示属性的解释，如上图所示。

我的最终的效果如图，

![效果图](http://7xljei.com1.z0.glb.clouddn.com/layout-2016-04-08-215909.png)

代码如下，
```java
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:scaleType="centerCrop"
        android:src="@drawable/card" />

    <TextView
        android:id="@+id/to"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="8dp"
        android:fontFamily="sans-serif-light"
        android:text="Happy BirthDay to Jarvis!"
        android:textAllCaps="false"
        android:textColor="@color/deep_purple_a700"
        android:textSize="30sp"
        android:textStyle="italic|bold" />

    <TextView
        android:id="@+id/from"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true"
        android:layout_margin="8dp"
        android:fontFamily="sans-serif-light"
        android:text="Chen Fuduo"
        android:textAllCaps="false"
        android:textColor="@color/deep_purple_a700"
        android:textSize="30sp"
        android:textStyle="italic|bold" />

</RelativeLayout>
```
需要注意的是ImageView的**`scaleType`**属性，我这里用的是**`centerCrop`**，关于**`centerCrop`**，它可以均匀一致的调节图像，会保持图像原始的比例。也就是 按比例扩大图片的size居中显示，使得图片长(宽)等于或大于View的长(宽) 。



