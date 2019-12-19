# FluctSDK-UnityPlugin 導入手順

## 対象Unityバージョン

* Unity 5.6.3f1 以上

## 対象OS

* iOS8.1 以上
* Android4.1 以上

## 事前準備
### アカウントと広告枠の作成
[fluct管理画面](https://fluct.jp/login)にて広告枠を作成し、営業担当から広告配信用のIDを受け取って下さい。

### プラグイン(FluctSDK-UnityPlugin.unitypackage)ダウンロード
[こちら](https://github.com/voyagegroup/FluctSDK-Unity/releases/latest)よりダウンロードして下さい。

## プロジェクトへの導入

### パッケージのインポート
Unity のメニューから、 `Assets` -> `Import Package` -> `Custom Package...`の順番でクリックし、 `FluctSDK-UnityPlugin.unitypackage`を選択しして下さい。

インポート画面で`Import`をクリックして下さい。

![Import画面](img/import_unitypackage.png)

### 依存ライブラリのインポート

Google公式の[unity-jar-resolver](https://github.com/googlesamples/unity-jar-resolver)の利用を推奨しています。  

#### iOS

Unity Editorのメニューから、`File` -> `Build Settings...`の順でクリックし、`Platform`を`iOS`に切り替えてください。  
次に`Assets` -> `Play Services Resolver` -> `iOS Resolver` -> `Settings`の順でクリックし、以下の設定を確認してください:

- `Podfile Generation` が有効になっていること
- `Cocoapods Integration` が `Xcode Workspace` または `Xcode Project` に設定されていること

なお、インポートされるライブラリの設定は `Assets/FluctSDK/Editor/FluctUnityPluginDependencies.xml` に記載されているため、必要に応じて変更してください。

#### Android

Unity Editorのメニューから、`File` -> `Build Settings...`の順でクリックし、`Platform` を`Android`に切り替えてください。  
次に `Assets` -> `Play Services Resolver` -> `Android Resolver` -> `Settings`の順でクリックし、以下の設定を確認してください:

- `Install Android Packages` が有効になっていること

以上を確認したら、`Assets` -> `Play Services Resolver` -> `Android Resolver` -> `Force Resolve`をクリックし、ライブラリのインポートを実行してください。

なお、インポートされるライブラリの設定は `Assets/FluctSDK/Editor/FluctUnityPluginDependencies.xml` に記載されているため、必要に応じて変更してください。

## 参考情報

### AndroidManifest.xmlの設定


Google Play Serviceの設定を追加します。
下記のタグを<application>エレメントの子に追加します。
なお、既に記述されている場合は記述不要となります。

```
<meta-data android:name="com.google.android.gms.version"
           android:value="@integer/google_play_services_version" />
```
