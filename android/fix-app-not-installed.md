# 署名付きAPKで「アプリはインストールされていません。」と出る場合の対処法
## How to fix "App not installed." problem.


署名付きAPK（Signed APK）を作成し、Android スマホに野良アプリとしてインストールしようとした時、
「アプリはインストールされていません。/ App not installed.」と出る場合がある。

この場合は、署名付きAPK発行ダイアログ、最終ページの `V1 (Jar Signature) ` にチェックを入れると解決する。
この際、`V2 (Full APK Signature)` の方にもチェックは必要。

```
Build > Generate Signed APK > [Module] > [Keystore] > [Setting]
```


### References
- https://stackoverflow.com/questions/4226132/app-not-installed-error-on-android