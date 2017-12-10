# Kotlin で `Parameter specified as non-null is null` エラーが出るときの対処法
## How to fix `Parameter specified as non-null is null` problem.

Kotlin は、null, non-null に厳しく、Nullable を常に意識したコーディングが求められる。
Kotlin で Android のプログラムを書くときは、継承元の java 関数の Nullable を気にしなければならない。

> Kotlin - Kotlin 間のプログラムでは、コンパイル時に指摘されるため、このエラーは起きない。  
> java - Kotlin 間ではこれが起きる可能性がある（Override Methodsなど）ので注意。

誤った記述をした場合、以下のようなエラーが出る。

```
Caused by: java.lang.IllegalArgumentException: Parameter specified as non-null is null: method kotlin.jvm.internal.Intrinsics.checkParameterIsNotNull, parameter savedInstanceState
```

これは、non-null のはずなのに null が渡されことを怒っているエラー。
java で書かれたソースコードを kotlin にコンバートしたときに起きるので注意。

Fragment の onCreateView を例に上げると...

### 間違った記述（java からコピペしてコンバートするとこうなる）

この場合はコンパイルエラーは出ないが、実行時に `IllegalArgumentException` が生じる。

```kotlin
override fun onCreateView(inflater: LayoutInflater, container: ViewGroup, savedInstanceState: Bundle) : View {
  // hogehoge
}
```

### 正しい記述

```kotlin
override fun onCreateView(inflater: LayoutInflater?, container: ViewGroup?, savedInstanceState: Bundle?) : View {
  // hogehoge
}
```

Android Studio で Override する場合は、
`Command(⌘) + n` → `Override Methods` → `目的の関数`
を選ぶと、正しい Nullable 指定がわかる。


### References
- https://qiita.com/mattak/items/51db2b200d57459a7273