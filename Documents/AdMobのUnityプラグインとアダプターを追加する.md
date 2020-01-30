## AdMobのUnityプラグインを追加する
[スタートガイド](https://developers.google.com/admob/unity/start?hl=ja)を参照して、Unityプラグインをインポートしてください。

`v3.18.0`以上をご利用の場合は、`Assets` -> `Play Services Resolver` -> `Android Resolver` -> `Settings`を選び、`Use Jetifier`の項目にチェックを入れてください。

## アダプターを追加する

### Androidのアダプター
`Assets/`配下の任意の場所に`Editor/FluctAndroidDependencies.xml`を作成し、
[FluctSDKの依存](https://github.com/voyagegroup/FluctSDK-Unity/blob/master/Dependencies/SampleFluctSdkAndroidForAdMobMediationDependencies.xml)を記述してください。

### iOSのアダプター
`Assets/`配下の任意の場所に`Editor/FluctIOSDependencies.xml`を作成し、
[FluctSDKの依存](https://github.com/voyagegroup/FluctSDK-Unity/blob/master/Dependencies/SampleFluctSdkIOSForAdMobMediationDependencies.xml)を記述してください。
