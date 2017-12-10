# 文字列から リソースID を取得する方法
## How to get resource ID from `String` text

プログラム上で `R.string.hogehoge` のようなリソースを取得する時、
`hogehoge` の部分を変数にしたくなる時がある。

例えば、カテゴリーに応じて `R.string.category_X (X=1..10)` のように呼び出したい文字列のIDに変数が含まれるケース。
Switch文で分けてもいいけど、変数が2つとかになると組合せがスゴイことになるのでやりたくない。

そんな場合にリソースIDを取得するには以下のようにする。

```
getResources().getIdentifier("文字列", "データ型", getPackageName());
文字列 ： リソースIDの文字列（R.string.XXX の「XXX」の部分）
データ型 ： リソースの型（R.XXX.hogehoge の「XXX」の部分）
```

これでリソースIDを取得すれば、`getResources().getString(取得したID)` てな感じでリソースを取り出せる。

データ型は例えば以下のような種類がある。

- `string`
- `color`
- `drawable`
- `layout`
- `array`
  - `<string-array>`
  - `<integer-array>`
- `dimen`
  - `<dimen>`
  - `<item name="xxx" format="float" type="dimen">`  
    ※ [put-float-value-in-xml-resources](put-float-value-in-xml-resources.md) で紹介した `item` を使ってサポートされていない float 型を定義する時

### References
- http://t-kashima.hateblo.jp/entry/20110203/1296748262
- https://stackoverflow.com/questions/7565108/android-referencing-string-array-using-another-string-with-getidentifier-and
- https://developer.android.com/guide/topics/resources/more-resources.html