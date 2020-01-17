## メディエーションするアドネットワークSDKを追加する
[AdMobのUnityプラグインとアダプターを追加する](AdMobのUnityプラグインとアダプターを追加する)で作成した、`Editor/FluctDependencies.xml`に下記の情報を追加してください。

```xml
<dependencies>
  <androidPackages>
	⋮
    <androidPackage spec="com.applovin:applovin-sdk:9.9.0">
        <repositories>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="jp.fluct.mediation:rewardedvideo-mediation-applovin:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="com.maio:android-sdk:1.1.10@aar">
        <repositories>
            <repository>https://imobile-maio.github.io/maven</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="jp.fluct.mediation:rewardedvideo-mediation-maio:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://imobile-maio.github.io/maven</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="net.nend.android:nend-sdk:5.1.1">
        <repositories>
            <repository>http://fan-adn.github.io/nendSDK-Android-lib/library</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="jp.fluct.mediation:rewardedvideo-mediation-nend:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>http://fan-adn.github.io/nendSDK-Android-lib/library</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="com.unity3d.ads:unity-ads:3.3.0">
        <repositories>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="jp.fluct.mediation:rewardedvideo-mediation-unityads:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="com.adcolony:sdk:4.1.0">
        <repositories>
            <repository>https://adcolony.bintray.com/AdColony</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="jp.fluct.mediation:rewardedvideo-mediation-adcolony:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://adcolony.bintray.com/AdColony</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="com.tapjoy:tapjoy-android-sdk:12.3.4@aar">
        <repositories>
            <repository>https://tapjoy.bintray.com/maven</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="jp.fluct.mediation:rewardedvideo-mediation-tapjoy:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://tapjoy.bintray.com/maven</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="com.glossom:glossom-ads-android:2.0.0">
        <repositories>
            <repository>https://github.com/glossom-dev/GlossomAds-Android/raw/master</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
    <androidPackage spec="jp.fluct.mediation:rewardedvideo-mediation-adcorsa:6.1.1">
        <repositories>
            <repository>https://voyagegroup.github.io/FluctSDK-Android/m2/repository</repository>
            <repository>https://github.com/glossom-dev/GlossomAds-Android/raw/master</repository>
            <repository>https://maven.google.com</repository>
            <repository>https://jcenter.bintray.com</repository>
            <repository>http://central.maven.org/maven2</repository>
        </repositories>
    </androidPackage>
	⋮
  </androidPackages>

  <iosPods>
	⋮
    <iosPod
        name="FluctSDK-MediationAdapter/AppLovin"
        version="6.0.0"
        minTargetSdk="9">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="AppLovinSDK"
        version="6.10.1"
        minTargetSdk="9">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="FluctSDK-MediationAdapter/maio"
        version="6.0.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="MaioSDK"
        version="1.4.8"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="FluctSDK-MediationAdapter/nend"
        version="6.0.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="NendSDK_iOS"
        version="5.3.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="FluctSDK-MediationAdapter/UnityAds"
        version="6.0.0"
        minTargetSdk="9">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="FluctSDK-MediationAdapter/Mintegral"
        version="6.0.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="MintegralAdSDK/RewardVideoAd"
        version="5.8.3"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="UnityAds"
        version="3.3.0"
        minTargetSdk="9">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="FluctSDK-MediationAdapter/Tapjoy"
        version="6.0.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="TapjoySDK"
        version="12.3.4"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="FluctSDK-MediationAdapter/AdColony"
        version="6.0.0"
        minTargetSdk="9">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="AdColony"
        version="4.1.1"
        minTargetSdk="9">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="FluctSDK-MediationAdapter/AdCorsa"
        version="6.0.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>

    <iosPod
        name="GlossomAds"
        version="2.0.0"
        minTargetSdk="8.1">
        <sources>
            <source>https://github.com/CocoaPods/Specs</source>
        </sources>
    </iosPod>
	⋮
  </iosPods>
</dependencies>
```

## 注意事項
基本的に、それぞれのSDKの最新バージョンをご利用ください。
ただし、iOSの開発環境として、Xcode11未満をお使いの場合、一部メディエーション先アドネットワークのライブラリにおいて最新バージョンをご利用することができません。
以下に該当するライブラリは、それに対応したバージョンをご利用ください。

- AdColony (v4.1.1)
	- [CHANGELOG](https://github.com/AdColony/AdColony-iOS-SDK/blob/master/CHANGELOG.md)
- maio (v1.4.8)
	- [リリースノート](https://github.com/imobile-maio/maio-iOS-SDK/releases)