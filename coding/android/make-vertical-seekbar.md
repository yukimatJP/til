# 縦方向の `SeekBar` を作る方法
## How to make vertical `SeekBar`.

layout の xml に記述した `SeekBar` の属性として、`android:rotation="270"` を追加するだけ。

ただし、そのままでは `SeekBar` の中心で270度回転するため、上にめり込んでしまう。
そこで、縦にしたときにいい感じに収まる親要素（`FrameLayout`とか）の中に `SeekBar` を置くといい感じ。

> `android:layout_width`, `android:layout_height` はそれぞれ逆転した値となっていることに注目。  
> `SeekBar` に `android:layout_gravity="center"` を追加しないと、どっかに消えてしまうので注意。

```xml
  <FrameLayout
    android:layout_width="100dp"
    android:layout_height="300dp" >

    <android.support.v7.widget.AppCompatSeekBar
      android:layout_width="300dp"
      android:layout_height="100dp"
      android:layout_gravity="center"
      android:rotation="270" />

  </FrameLayout>
```

### References
- https://stackoverflow.com/questions/31329970/changing-the-length-of-a-seekbar-in-xml