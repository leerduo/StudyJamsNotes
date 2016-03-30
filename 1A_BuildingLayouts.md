
本部分主要包含三个部分的内容：
> * Select Views
* Style Views
* Position Views

也就是包含了其一什么是Android中的View；其二是怎么改变View，比如文字的大小，样式，颜色，改变图片等等；其三是如何在屏幕中摆放这些View。

简单来说，一个View是Android手机屏幕上用来展示内容的矩形，它可以是一个图片，一段文字，亦或是一个按钮。所有的这些View组成Android屏幕的布局(Layout)。

View是Android手机屏幕的一块矩形，这个在理论上是看不到边框的，但是可以画出矩形的边框，如下图，绿色边框圈起来的即是View矩形区域。

![View是矩形的](http://7xljei.com1.z0.glb.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20160330210558.png)

本节主要介绍了TextView和ImageView以及Button，它们的命名符合驼峰命名规范。

xml是可扩展标记语言。

单位dp的全称是密度无关像素(density-independent pixels)。

![dp@pixel](http://7xljei.com1.z0.glb.clouddn.com/dp%26piexl_%E5%89%AF%E6%9C%AC.png)

图中每个方块代表一个像素，现在假设有个3个像素高宽的Button，可以看到在不同分辨率的设备上，大小不一致，使用dp可以解决这个问题。

sp的全称是比例无关像素(scale indepent pixels)，sp用来设定文字的大小。

接着介绍了很多TextView的属性，如下，
```xml
<TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@android:color/darker_gray"
        android:text="Happy Birthday!"
        android:textAppearance="?android:attr/textAppearanceLarge"
        android:textColor="@color/colorAccent"
        android:textSize="40sp"
        android:textStyle="bold" />
```

接下来介绍了ImageView，需要留意的是`scaleType`这个属性，推荐使用的是属性值为`centerCrop`这个。

练习的ImageView的代码如下，

```xml
<ImageView
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:src="@mipmap/view2"
        android:scaleType="centerCrop"
        />
```



