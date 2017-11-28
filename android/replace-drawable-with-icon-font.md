# 単色 `Drawable` を IconFont に置き換える方法
## How to replace single-color `Drawable` with Icon Font

Androidにおいて、
Drawable は `xxx-hdpi ~ mdpi` とたくさんのサイズを用意しないといけないし、
容量も食うしで面倒。
しかも Drawable は標準ではフォルダを掘れないから、
フォルダがアイコンまみれで見にくくなる（サブフォルダを作って hack する方法はあるにはあるっぽい）。

そこで、IconFont（アイコンをフォント化したもの、[FontAwesome](http://fontawesome.io/)が代表的）を使ってみる。

> この方法は単色アイコン（背景透過）にしか適用できないので注意。

利点としては、
- 単色アイコンのようなシンプルな画像に関しては png などより容量が軽くなる傾向がある
- サイズ違いを準備する必要がない（フォントサイズを指定することでアイコンサイズを変更できる）
- 色違いを準備する必要がない（フォントカラーを指定することでアイコン色を変更できる）
- なにせ IconFont にまとめるとファイルが１つになる → Drawable に画像ファイルが増えすぎない

### IconFontの使い方

`TextView` などに文字として入れる。
例えば、FontAwesome で提供されている、Githubのロゴ（Unicode: f09b）を入れるとすると

```
assets/font/fontAwesome.ttf
```

のように FontAwesome の .ttf ファイルを置いて

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
  xmlns:android="http://schemas.android.com/apk/res/android"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:orientation="vertical">
 
  <TextView
    android:id="@+id/tv_icon"
    android:layout_width="24dp"
    android:layout_height="24dp"
    android:text="\uf09b"
    android:textSize="24sp" />

</LinearLayout>
```

みたいな感じで書く。

んで、プログラムコード中で TypeFace を変えてあげればOK。

```java
TextView tv = (TextView) findViewById(R.id.tv_icon);
Typeface tf = Typeface.createFromAsset(getContext().getAssets(), "font/fontAwesome.ttf");
tv.setTypeface(tf);
```

ちなみに、自作アイコンを作るには [IcoMoon](https://icomoon.io/) が有用。
自分のアプリに必要なだけ IconFont としてダウンロードが可能。

### References
- https://qiita.com/motodimago/items/8f10a7ddb3bb8f523bfc
- https://shufulife.com/icomoon/