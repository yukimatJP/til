# `GoogleAuthUtil.getToken(...)` でトークンが取得できない場合の対処法
## How to get token using `GoogleAuthUtil.getToken(...)` .


GoogleAuthUtilを使ってOAuth 2.0 tokenを取得する場合、上手く取得できない場合がある。

おそらく API が利用できない状態になっていると思われるので、Google Cloud Platform の API コンソールに行って、**OAuth 2.0 クライアント ID** が作成されているかどうかを確認する。

```
Google Cloud Platform > APIとサービス > 認証情報
```

このクライアントIDに、デバッグ用、リリース用 それぞれの **SHA-1 fingerprint** が登録されていなければ、`GoogleAuthUtil.getToken(...)` は通らない。

なお、**SHA-1 fingerprint** は、環境の変化に応じて 当然変わる。随時アップデートしなければいけない。

- ビルドするPCを変更した
- Keystore を変更した

### SHA-1 fingerprint の取得方法

#### ◯ デバッグ用
1. Android Studio 右上の「Gradle」タブを開く
2. `ROOT folder(:app) > Tasks > android > signingReport` をダブルクリック
3. Android Studio 右下の Gradle Console の中に **SHA-1 fingerprint** の情報が出ている

もしくは、以下のコマンドを実行する。

```shell
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
```


#### ◯ リリース用

以下のコマンドを実行する。
```shell
keytool -list -v -keystore "key-store-path" -alias "key-alias"
    key-store-path: ***.jks のある場所
    key-alias:      ***.jks に登録されているエイリアス
```
パスワード等を聞かれるので登録されている情報に基づいて入力する。
出力結果の中に **SHA-1 fingerprint** の情報が出ているはず



### References
- https://stackoverflow.com/questions/34933380/sha1-key-for-debug-release-android-studio-mac