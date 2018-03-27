# 動画リワードの実装

## 接続アドネットワーク
* AppLovin
* maio
* nend
  * iOS8.1以降
* UnityAds

## 事前準備

### groupId、unitIdに関して
貴社アプリのgroupId, unitIdは弊社担当営業にお問い合わせください。


## プロジェクトへの導入

### パッケージのインポート

1. 当リポジトリをclone

2. 貴社アプリのプロジェクトを起動後に当リポジトリに移動して以下のコマンドを実行

  `$ open FluctSDK-UnityPlugin.unitypackage`

3. ImportUnityPackageが起動するので`Import`をクリック


## 広告表示の実装例

```C#
using UnityEngine;
using System.Reflection;
using Fluct;

public class RewardedVideoSceneController : MonoBehaviour
{
#if UNITY_ANDROID
    private string groupId = ""; // Android用 groupId
    private string unitId = ""; // Android用 unitId
#elif UNITY_IOS
    private string groupId = ""; // iOS用 groupId
    private string unitId = ""; // iOS用 unitId
#else
    private string groupId = ""; // ビルドエラー回避用
    private string unitId = ""; // ビルドエラー回避用
#endif
    private string userId = ""; // 追跡用のId(貴社アプリ内のユーザID等をご利用ください) null可

    private RewardedVideo rv;

    void Start()
    {
        // 初期処理
        rv = new RewardedVideo(groupId, unitId);

        // イベントハンドラ設定
        rv.OnDidLoad += HandleDidLoad;
        rv.OnDidOpen += HandleDidOpen;
        rv.OnDidClose += HandleDidClose;
        rv.OnShouldReward += HandleShouldReward;
        rv.OnDidFailToLoad += HandleDidFailToLoad;
        rv.OnDidFailToPlay += HandleDidFailToPlay;
    }

    void OnDestroy()
    {
        // イベントハンドラ解除
        rv.OnDidLoad -= HandleDidLoad;
        rv.OnDidOpen -= HandleDidOpen;
        rv.OnDidClose -= HandleDidClose;
        rv.OnShouldReward -= HandleShouldReward;
        rv.OnDidFailToLoad -= HandleDidFailToLoad;
        rv.OnDidFailToPlay -= HandleDidFailToPlay;
    }

    /// <summary>
    /// 広告読み込み
    /// </summary>
    public void Load()
    {
        rv.Load(targeting: new AdRequestTargeting(userId));
    }

    /// <summary>
    /// 広告再生
    /// </summary>
    public void Present()
    {
        // 広告再生可能の場合
        if (rv.HasAdAvailable())
        {
            // 広告再生
            rv.Present();
        }
    }

    /// <summary>
    /// 広告読み込み完了の際に呼ばれます
    /// </summary>
    public void HandleDidLoad(object sender, RewardedVideoEventArgs e)
    {
        Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3} instancetID={4}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId, this.GetInstanceID());
    }

    /// <summary>
    /// 広告画面表示直後に呼ばれます
    /// </summary>
    public void HandleDidOpen(object sender, RewardedVideoEventArgs e)
    {
        Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3} instancetID={4}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId, this.GetInstanceID());
    }

    /// <summary>
    /// 広告画面を閉じた直後に呼ばれます
    /// </summary>
    public void HandleDidClose(object sender, RewardedVideoEventArgs e)
    {
        Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3} instancetID={4}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId, this.GetInstanceID());
    }

    /// <summary>
    /// リワード付与すべき際に呼ばれます
    /// </summary>
    public void HandleShouldReward(object sender, RewardedVideoEventArgs e)
    {
        Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3} instancetID={4}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId, this.GetInstanceID());
    }

    /// <summary>
    /// 広告読み込み失敗の際に呼ばれます
    /// </summary>
    public void HandleDidFailToLoad(object sender, RewardedVideoErrorEventArgs e)
    {
        Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3} errorMessage={4} instancetID={5}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId, e.ErrorCode, this.GetInstanceID());
    }

    /// <summary>
    /// 広告表示失敗の際に呼ばれます
    /// </summary>
    public void HandleDidFailToPlay(object sender, RewardedVideoErrorEventArgs e)
    {
        Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3} errorMessage={4} instancetID={5}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId, e.ErrorCode, this.GetInstanceID());
    }
}

```


## 各種イベント通知に関して

* イベントを設定することでPluginから広告のイベント通知を受け取ることが可能になります。
* イベントの設定の仕方に関しては、広告表示の実装例をご参照ください。


| イベント        | 通知タイミング       |
|-----------------|----------------------|
| OnDidLoad       | 広告読み込み完了の際 |
| OnDidFailToLoad | 広告読み込み失敗の際 |
| OnDidOpen       | 広告画面表示直後     |
| OnShouldReward  | リワード付与すべき際 |
| OnDidClose      | 広告画面を閉じた直後 |
| OnDidFailToPlay | 広告表示失敗の際     |

### エラー発生時のエラー内容について

`OnDidFailToLoad`, `OnDidFailToPlay` のイベントはエラー情報を含みます。
詳細については、各OS毎のエラーコードをご確認下さい 

* [iOS](https://github.com/voyagegroup/FluctSDK-iOS/wiki/Swift%E3%81%A7%E3%81%AE%E5%8B%95%E7%94%BB%E3%83%AA%E3%83%AF%E3%83%BC%E3%83%89%E5%BA%83%E5%91%8A%E5%AE%9F%E8%A3%85#%E3%82%A8%E3%83%A9%E3%83%BC%E3%82%B3%E3%83%BC%E3%83%89%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6)
* [Android](https://github.com/voyagegroup/FluctSDK-Android/wiki/%E5%8B%95%E7%94%BB%E3%83%AA%E3%83%AF%E3%83%BC%E3%83%89%E5%BA%83%E5%91%8A%E5%AE%9F%E8%A3%85#%E3%82%A8%E3%83%A9%E3%83%BC%E3%82%B3%E3%83%BC%E3%83%89%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6)