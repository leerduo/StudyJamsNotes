title: 2A_Making an App Interactive
date: 2016-04-13 23:08
---

本部分主要介绍两个部分的知识，一是用户如何与控件交互，二是熟悉Java的方法、变量等。

程序从一个订购咖啡的程序坐起，由简单到复杂。

先是实现这样的效果，

![效果1](http://7xljei.com1.z0.glb.clouddn.com/310800151919686010.jpg)

布局代码是这样的，

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center_horizontal"
    android:orientation="vertical">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="数量"
        android:layout_margin="16dp"
        android:textSize="16sp"
        />

    <TextView
        android:id="@+id/tvQuantity"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:layout_margin="16dp"
        android:textSize="16sp"
        android:textColor="@android:color/black"
        />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="订购"
        android:layout_margin="16dp"
        android:onClick="submitOrder"
        />
</LinearLayout>
```

初始时订购的数量为0，当点击"订购"按钮时，显示订购的数量。

那么就涉及到按钮的点击事件，这里通过`onClick`属性实现，在逻辑代码中，这样做，

```java
public void submitOrder(View view) {
        display(88);
    }

    private void display(int number) {
        TextView tvQuantity = (TextView) findViewById(R.id.tvQuantity);
        tvQuantity.setText("" + number);
    }
```

现在加上咖啡的价格，如下，

![效果2](http://7xljei.com1.z0.glb.clouddn.com/538959813842935768.jpg)

布局代码如下：

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center_horizontal"
    android:orientation="vertical">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="数量"
        android:layout_margin="16dp"
        android:textSize="16sp"
        />

    <TextView
        android:id="@+id/tvQuantity"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:layout_margin="16dp"
        android:textSize="16sp"
        android:textColor="@android:color/black"
        />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="价格"
        android:layout_margin="16dp"
        android:textSize="16sp"
        />

    <TextView
        android:id="@+id/tvPrice"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:layout_margin="16dp"
        android:textSize="16sp"
        android:textColor="@android:color/black"
        />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="订购"
        android:layout_margin="16dp"
        android:onClick="submitOrder"
        />


</LinearLayout>
```

初始的时候，咖啡的数量和价格都为0，当点击"订购"按钮的时候，显示数量和价格，

```java
public void submitOrder(View view) {
        displayQuantity(1);
        displayPrice(1*3.14f);
    }

    private void displayPrice(float price) {
        TextView tvPrice = (TextView) findViewById(R.id.tvPrice);
        tvPrice.setText(NumberFormat.getCurrencyInstance().format(price));
    }

    private void displayQuantity(int number) {
        TextView tvQuantity = (TextView) findViewById(R.id.tvQuantity);
        tvQuantity.setText("" + number);
    }
```

这句代码将价格的数值格式化显示了，

```java
NumberFormat.getCurrencyInstance().format(price);
```

在上面的代码中，咖啡的数量和价格都是一个字面值常量，现在用一个变量更替，这样，代码的鲁棒性就会更好。

```java
public void submitOrder(View view) {
        int numberOfCoffees = 2;
        float priceOfCoffees = 3.14f;
        displayQuantity(numberOfCoffees);
        displayPrice(numberOfCoffees * priceOfCoffees);
    }
```

程序崩溃后的日志查看，布局中按钮的`onclick`属性值为`submitOrder`，将代码中的这个方法名改为`submitOrder1`得到下面的日志。

```
java.lang.IllegalStateException: 
Could not find method submitOrder(View)
in a parent or ancestor Context for 
android:onClick attribute defined on view class android.support.v7.widget.AppCompatButton
 ```
 
可以发现，提示我们在Activity中找不到这个`submitOrder(View)`方法。

增加断点调试程序。

现在增加两个按钮，分别是"增加"和"减少"咖啡的作用，布局如下，

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center_horizontal"
    android:orientation="vertical">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="数量"
        android:layout_margin="16dp"
        android:textSize="16sp"
        />

    <Button
        android:layout_width="48dp"
        android:layout_height="48dp"
        android:text="+"
        android:onClick="incrementQuantity"
        />

    <TextView
        android:id="@+id/tvQuantity"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:textSize="16sp"
        android:textColor="@android:color/black"
        />

    <Button
        android:layout_width="48dp"
        android:layout_height="48dp"
        android:text="-"
        android:onClick="decrementQuantity"
        />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="价格"
        android:layout_margin="16dp"
        android:textSize="16sp"
        />

    <TextView
        android:id="@+id/tvPrice"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:layout_margin="16dp"
        android:textSize="16sp"
        android:textColor="@android:color/black"
        />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="订购"
        android:layout_margin="16dp"
        android:onClick="submitOrder"
        />


</LinearLayout>
```

逻辑代码如下，

```java
package me.jarvischen.studyjams;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.support.v7.widget.AppCompatCheckBox;
import android.support.v7.widget.AppCompatTextView;
import android.view.View;
import android.widget.TextView;
import android.widget.Toast;

import java.text.NumberFormat;

public class MainActivity extends AppCompatActivity {

    private int quantity = 2;
    private float priceOfCoffees = 3.14f;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.coffee_layout);
        initView();
    }

    private void initView() {
        displayQuantity(quantity);
        displayPrice(quantity * priceOfCoffees);
    }

    public void incrementQuantity(View view) {
        quantity++;
        displayQuantity(quantity);
        displayPrice(quantity * priceOfCoffees);
    }

    public void decrementQuantity(View view) {
        if (quantity > 0) {
            quantity--;
            displayQuantity(quantity);
            displayPrice(quantity * priceOfCoffees);
        } else {
            Toast.makeText(this, "咖啡的订购数量不得小于0杯", Toast.LENGTH_SHORT).show();
        }

    }

    public void submitOrder(View view) {
        displayQuantity(quantity);
        displayPrice(quantity * priceOfCoffees);
    }

    private void displayPrice(float price) {
        TextView tvPrice = (TextView) findViewById(R.id.tvPrice);
        tvPrice.setText(NumberFormat.getCurrencyInstance().format(price));
    }

    private void displayQuantity(int number) {
        TextView tvQuantity = (TextView) findViewById(R.id.tvQuantity);
        tvQuantity.setText("" + number);
    }
}
```

需要注意的是全局变量和局部变量的区别，另外，这里当咖啡小于0的时候，做了判断。

![效果3](http://7xljei.com1.z0.glb.clouddn.com/302615203302842694.jpg)