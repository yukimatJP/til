# プログラム上でフルスクリーンモードに切り替える方法
## How to switch full screen mode programmatically.

プログラム上でステータスバー領域も含めてフルスクリーンに切り替える場合は、
以下の一行を追加する。

```java
getWindow().addFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN);
```

Fragment からも変更可能。その場合は `getActivity()` する必要がある。

```java
getActivity().getWindow().addFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN);
```

### References
- https://stackoverflow.com/questions/10803973/programmatically-make-app-full-screen-in-android