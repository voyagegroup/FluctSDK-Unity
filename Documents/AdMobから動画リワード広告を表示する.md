## 動画リワード広告の表示
### AdMobのメディエーショングループのカスタムイベントでFluctSDKを使用する際の設定する内容

eCPMの値は弊社担当コンサルタントより指定された数字を入力ください。`GroupID`と`UnitID`は弊社担当コンサルタントにお問い合わせください。

#### iOSの場合

| 項目 | 入力内容 |
|:-----|:----- |
| Class Name | `GADMediationAdapterFluct`  |
| Parameter | `GroupID`,`UnitID` |

#### Androidの場合

| 項目 | 入力内容 |
|:-----|:----- |
| Class Name | `jp.fluct.mediation.gma.FluctMediationRewardedVideoAdAdapter` |
| Parameter | `GroupID`,`UnitID` |

#### 入力するParameterについて

```
GroupID: 1000104107
UnitID: 1000160561
```

の場合

```
1000104107,1000160561
```

と`Parameter`に入力してください。

### 広告の表示
[AdMobのガイド](https://developers.google.com/admob/unity/rewarded-ads?hl=ja)を参照してください。
[従来のAPI](https://developers.google.com/admob/unity/rewarded-video?hl=ja)にも対応しています。