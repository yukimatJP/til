# resources/values XML で float のデータ扱う方法
## How to put float value in resources/values XML.

resources/values の XML では `integer` というタイプはあるけれど `float` はない。 
`float` を XML で定義しておきたい場合は以下のように、`item` をつかって表現する。
属性として、`fotmat` で変数の型、`type` で変数の種類を定義する。

```xml
<resources>
  <item name="float_value" format="float" type="dimen">10.0</item>
</resources>
```

こう定義しておけば、他のXMLから以下のように呼び出すことができる。

```xml
@dimen/float_value
```

また、これをプログラムから呼び出すためには、`getResources().getDimension(...)` は使えない。
`getResources().getValue`と、`TypedValue` 型の変数を用いて以下のように取得する。

```java
TypedValue typedValue = new TypedValue();
getResources().getValue(R.dimen.float_value, typedValue, true);
float value = typedValue.getFloat();  
```

### References
- https://stackoverflow.com/questions/3282390/add-floating-point-value-to-android-resources-values