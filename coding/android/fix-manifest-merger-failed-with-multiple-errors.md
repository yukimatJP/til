# `Manifest merger failed with multiple errors` と出たときの対処方法
## How to solve `Manifest merger failed with multiple errors` problem.

Android Studio を使っていて、新しく外部SDKを導入する時、
Messages タブに以下のエラーが出てどうしようもない状態に陥ることがある。

```
Information:Gradle tasks [......]
Error:Execution failed for task ':app:processDebugManifest'.
> Manifest merger failed with multiple errors, see logs
Information:BUILD FAILED
```

### エラーの実態

"see logs" という割に、押してもログに飛ぶこともなく、
どこにログがあるとも教えてくれるわけでもなく...。どないなってるねんと。

Manifest merger failed なので、おそらく Manifest 関連のエラーなのだろう。
しかし、SDKのインポートでは gradle ファイルしか触ってないのに、なぜ Manifest がエラーを吐くのか。

これは、新しくインポートした SDK の中にも AndroidManifest.xml が含まれており、競合が起きてしまっている、という状態らしい。

### エラーの確認方法

エラーの確認方法については、[この動画](https://www.youtube.com/watch?v=5JFswAfn8lk) が、わかりやすい。

AndroidManifest.xml を開いて、エディタ下部にあるタブ一覧の中から Merged Manifest のタブを開く（通常編集しているタブは Text）。

そうすると、右側のエリアにログが残されており、
おそらくこの中に Manifest merger faild の原因となっているエラーが表示されているはず。
このエラーはクリックすると解決策を提示してくれるので、案内に従って改善すれば良い。

### References
- https://www.youtube.com/watch?v=5JFswAfn8lk