# `ViewPager` でスワイプを禁止する
## How to disable swipe action on `ViewPager`

`ViewPager` でスワイプによる次のページへの移動を無効化するには、`ViewPager`のサブクラスを作成する必要がある。

```kotlin
class NonSwipeableViewPager(context: Context, attrs: AttributeSet) : ViewPager(context, attrs) {

  override fun onInterceptTouchEvent(ev: MotionEvent?): Boolean = false

  override fun onTouchEvent(ev: MotionEvent?): Boolean = false

}
```
kotlinで書くとめっちゃ短く書ける。

### References
- https://github.com/shortstack/HackerTracker/blob/ac1ea4f0295fe2f4e5077d3acfd2dc719ed387c2/hackertracker/src/main/java/com/shortstack/hackertracker/View/NonSwipeableViewPager.kt