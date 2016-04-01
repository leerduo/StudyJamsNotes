ViewGroup是用来摆放View的，每个ViewGroup如何摆放View，有其自身的规则；同View一样，也是一块矩形区域，有高度和宽度，另外，ViewGroup也属于View。

LinearLayout有水平和垂直两种摆放其子View的方式。

RelayoutLayout根据View间的相对位置来摆放View。

```xml
xmlns:android="http://schemas.android.com/apk/res/android"
```
这句代码是xml命名空间声明，指定下面使用的`android:`是android的属性。

LinearLayout中layout_weight属性的使用，`layout_weight`属性表示View占据父View空间的权重，如，
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"
        android:background="@color/yellow_50"
        android:text="Number 1"
        android:textSize="40sp"
        android:textStyle="bold"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"
        android:background="@color/teal_500"
        android:text="Number 2"
        android:textSize="40sp"
        android:textStyle="bold|italic"
        />


    <TextView
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"
        android:background="@color/blue_300"
        android:text="Number 3"
        android:textSize="40sp"
        android:textStyle="italic"
        />

</LinearLayout>
```

![效果图](http://7xljei.com1.z0.glb.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20160401220134.png)

因为每个View的layout_weight属性都是1，所以三个TextView平分了。

更改下代码如下：

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"
        android:background="@color/yellow_50"
        android:text="Number 1"
        android:textSize="40sp"
        android:textStyle="bold"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="2"
        android:background="@color/teal_500"
        android:text="Number 2"
        android:textSize="40sp"
        android:textStyle="bold|italic"
        />


    <TextView
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1"
        android:background="@color/blue_300"
        android:text="Number 3"
        android:textSize="40sp"
        android:textStyle="italic"
        />

</LinearLayout>
```
那么效果图如下，

![效果图](http://7xljei.com1.z0.glb.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20160401220658.png)

中间的TextView的layout_weight属性是2，所以它占据了一半，其他的两个各占四分之一。

对于水平分布，也是同样的道理，只要将layout_width设置为0dp再去设置layout_weight属性即可。

再比如，
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@color/yellow_500"
        android:text="text"
        android:textSize="20sp"
        android:textStyle="bold"
        />

    <EditText
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:hint="please input words."
        />


    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@color/blue_300"
        android:text="send"
        android:textSize="20sp"
        android:textStyle="italic"
        />

</LinearLayout>
```
![效果图](http://7xljei.com1.z0.glb.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20160401221415.png)


常见的RelativeLayout的属性，

* 第一类:属性值为true或false
```xml
android:layout_centerHrizontal	水平居中
android:layout_centerVertical	垂直居中
android:layout_centerInparent	相对于父元素完全居中
android:layout_alignParentBottom	贴紧父元素的下边缘
android:layout_alignParentLeft	贴紧父元素的左边缘
android:layout_alignParentRight	贴紧父元素的右边缘
android:layout_alignParentTop	贴紧父元素的上边缘
android:layout_alignWithParentIfMissing	如果对应的兄弟元素找不到的话就以父元素做参照物
```
* 第二类：属性值必须为id的引用名“@id/id-name”
```xml
android:layout_below	在某元素的下方
android:layout_above	在某元素的的上方
android:layout_toLeftOf	在某元素的左边
android:layout_toRightOf	在某元素的右边
android:layout_alignTop	本元素的上边缘和某元素的的上边缘对齐
android:layout_alignLeft	本元素的左边缘和某元素的的左边缘对齐
android:layout_alignBottom	本元素的下边缘和某元素的的下边缘对齐
android:layout_alignRight	本元素的右边缘和某元素的的右边缘对齐
```
* 第三类：属性值为具体的像素值，如30dip，40px
```xml
android:layout_marginBottom	离某元素底边缘的距离
android:layout_marginLeft	离某元素左边缘的距离
android:layout_marginRight	离某元素右边缘的距离
android:layout_marginTop	离某元素上边缘的距离
```

padding由View自身完成，margin由View所在的ViewGroup完成。

padding和margin的值最好设置为8的倍数。




