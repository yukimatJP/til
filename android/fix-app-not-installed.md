# 署名付きAPKで「アプリはインストールされていません。」と出る場合の対処法
## How to fix "App not installed." problem.

署名付きAPKを発行して「アプリはインストールされていません。/ App not installed.」と出る場合、
署名付きAPK発行ダイアログ（下記）の最終ページで、`V1 (Jar Signature) `にチェックを入れる。

```
Build > Generate Signed APK > [Module] > [Keystore] > [Setting]
```

## 参考
- https://stackoverflow.com/questions/4226132/app-not-installed-error-on-android