# インタースティシャル広告の実装

## Prefabで実装する場合

Assets/Prefabsにある`FluctStartShowInterstitial.prefab`をDrag&DropでSceneに追加します。

![FluctStartShowInterstitial.prefabをSceneに追加](img/dd_prefab_interstitial.png)

Inspectorでの設定

![Inspector上での設定画面(インターステシャル)](img/inspector_config_interstitial.png)

`YOUR_MEDIA_ID`の部分は発行された本番用`MediaID`を設定してください。

## コード実装する場合(実装例)

```
private FluctInterstitial interstitial;
void Start () {
  interstitial = gameObject.AddComponent<FluctInterstitial>();
}

void OnGUI () {
  if (GUI.Button(new Rect(180, 300, 200, 100), "ShowInterstitial")) {
    interstitial.ShowInterstitial("YOUR_MEDIA_ID");
  }
}
```

`YOUR_MEDIA_ID`の部分は発行された本番用`MediaID`を設定してください。

