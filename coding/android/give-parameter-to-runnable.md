# `Runnable` にパラメータを渡す方法
## How to give parameter to `Runnable`.

`Handler().postDelayed(..., delay)` を使って遅延実行するときや、`Thread` を立てるときに `Runnable` にパラメータを渡したくなる。
（かと言って `Runnable` を継承したクラスを作るほどではない...）

そこで、無名クラス宣言中にパラメータの setter を定義するといい感じ。

```java
int number;
String text;
int delay;

new Handler().postDelayed(new Runnable() {
    int number;
    String text;

    public Runnable setParams(int number, String text) {
      this.number = number;
      this.text = text;
      return this; // 自分自身を返す
    }

    @Override
    public void run() {
      // 実際の処理
    }
  }.setParams(number, text),
  delay
);
```

ちなみにそんな回りくどいことはせずに、
Runnable の外側の変数を final 宣言すればいい説はある。

```java
final int number;
final String text;
int delay;

new Handler().postDelayed(new Runnable() {
    @Override
    public void run() {
      // 実際の処理
    }
  },
  delay
);

```


### References
- http://futurismo.biz/archives/2752