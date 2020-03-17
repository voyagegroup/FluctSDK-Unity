## メディエーションするアドネットワークSDKを追加する

弊社担当コンサルタントに指定されたアドネットワークの追加をお願いします。

## 接続アドネットワーク

### iOS

- AppLovin
    - iOS9以上
- Maio
    - Xcode10以下をしようしている場合はMaioSDKのバージョン1.4.8をご使用ください
        - [リリースノート](https://github.com/imobile-maio/maio-iOS-SDK/releases)
- Nend
- UnityAds
    - iOS9以上
    - Xcode10以上をお使いください
- Tapjoy
- AdColony
    - iOS9以上
    - Xcode10以下のバージョンで開発している場合はAdColonyのSDKのバージョン4.1.1をご使用ください
        - [CHANGELOG](https://github.com/AdColony/AdColony-iOS-SDK/blob/master/CHANGELOG.md)
- AdCorsa
- Mintegral

### Android

- AppLovin
- Maio
- Nend
- UnityAds
- Tapjoy
- AdColony
- AdCorsa

## アダプターを追加する

1. [最新のリリースページ](https://github.com/voyagegroup/FluctSDK-Unity/releases/latest)より`FluctSDK-MediationAdapters.zip`をダウンロードして解凍してください。

2. Unity のメニューから、 `Assets` -> `Import Package` -> `Custom Package...`の順番でクリックしてください。

![screenshot01](./img/import_admob_mediation_unitypackage_01.png)

3. ダウンロードしたFluctSDK-MediationAdaptersディレクトリからメディエーションするアドネットワークのunitypackageを選択してimportしてください。

![screenshot02](./img/import_fluctsdk_mediation_unitypackage_01.png)

4. importされるファイルが選択できる画面が出るので、`import`を押してください。これで導入完了です。

![screenshot03](./img/import_fluctsdk_mediation_unitypackage_02.png)
