## AdMobのUnityプラグインを追加する
[スタートガイド](https://developers.google.com/admob/unity/start?hl=ja)を参照して、Unityプラグインをインポートしてください。

`v3.18.0`以上をご利用の場合は、`Assets` -> `Play Services Resolver` -> `Android Resolver` -> `Settings`を選び、`Use Jetifier`の項目にチェックを入れてください。

## アダプターを追加する
`Assets/`配下の任意の場所に`Editor/FluctDependencies.xml`を作成し、下記のように記述してください。

```xml
<dependencies>
  <androidPackages>
    <!--Androidに対応する場合-->
    <!--最新のSDKバージョンをご利用ください-->
    <androidPackage spec="jp.fluct:FluctSDK:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <!--最新のSDKバージョンをご利用ください-->
    <androidPackage spec="jp.fluct.mediation.gma:gma-mediation:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <!--最新のSDKバージョンをご利用ください-->
    <androidPackage spec="jp.fluct.fluctsdk:banner:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
  </androidPackages>

  <iosPods>
    <!--iOSに対応する場合-->
    <!--最新のSDKバージョンをご利用ください-->
    <iosPod
        name="GoogleMobileAdsMediationFluct"
        version="6.0.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>
    <!--最新のSDKバージョンをご利用ください-->
    <iosPod
        name="FluctSDK"
        version="6.0.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>
  </iosPods>
</dependencies>
```
### 注意事項
基本的に、それぞれのプラットフォームにおける最新バージョンのSDKをご利用ください。
最新バージョンはこちらをご参照ください。[iOS](https://github.com/voyagegroup/FluctSDK-iOS#fluctsdk-release-note), [Android](https://github.com/voyagegroup/FluctSDK-Android#fluctsdk-release-note)
