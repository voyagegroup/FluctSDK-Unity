# 動画リワードの実装

## 対象OS
* iOSのみ

※ Androidは未対応

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

public class RewardedVideoCall : MonoBehaviour
{
	private FluctRewardedVideo rv;
	private string groupId = "";  // 貴社groupId
	private string unitId = "";   // 貴社unitId
	private string userId = ""; // 追跡用のId(貴社アプリ内のユーザID等をご利用ください) null可
	private RewardedVideo rv;

	public void Start()
	{

		FluctSDK.Initialize();

		rv = new RewardedVideo(groupId, unitId);
		// イベントの設定を行います
		rv.OnDidLoad += HandleDidLoad;
		rv.OnWillAppear += HandleWillAppear;
		rv.OnDidAppear += HandleDidAppear;
		rv.OnWillDisappear += HandleWillDisappear;
		rv.OnDidDisappear += HandleDidDisappear;
		rv.OnShouldReward += HandleShouldReward;
		rv.OnDidFailToLoad += HandleDidFailToLoad;
		rv.OnDidFailToPlay += HandleDidFailToPlay;
	}

	void OnDestroy()
	{
		// イベントハンドラの解除を行います
		rv.OnDidLoad -= HandleDidLoad;
		rv.OnWillAppear -= HandleWillAppear;
		rv.OnDidAppear -= HandleDidAppear;
		rv.OnWillDisappear -= HandleWillDisappear;
		rv.OnDidDisappear -= HandleDidDisappear;
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
			buttonPlay.interactable = false;
		}
	}

	/// <summary>
	/// 広告読み込み完了の際に呼ばれます
	/// </summary>
	public void HandleDidLoad(object sender, RewardedVideoEventArgs e)
	{
		Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId);
	}

	/// <summary>
	/// 広告画面表示直前に呼ばれます
	/// </summary>
	public void HandleWillAppear(object sender, RewardedVideoEventArgs e)
	{
		Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId);
	}

	/// <summary>
	/// 広告画面表示直後に呼ばれます
	/// </summary>
	public void HandleDidAppear(object sender, RewardedVideoEventArgs e)
	{
		Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId);
	}

	/// <summary>
	/// 広告画面を閉じる直前に呼ばれます
	/// </summary>
	public void HandleWillDisappear(object sender, RewardedVideoEventArgs e)
	{
		Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId);
	}

	/// <summary>
	/// 広告画面を閉じた直後に呼ばれます
	/// </summary>
	public void HandleDidDisappear(object sender, RewardedVideoEventArgs e)
	{
		Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId);
	}

	/// <summary>
	/// リワード付与すべき際に呼ばれます
	/// </summary>
	public void HandleShouldReward(object sender, RewardedVideoEventArgs e)
	{
		Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId);
	}

	/// <summary>
	/// 広告読み込み失敗の際に呼ばれます
	/// </summary>
	public void HandleDidFailToLoad(object sender, RewardedVideoErrorEventArgs e)
	{
		Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3} errorCode={4} errorMessage={5}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId, e.ErrorCode, e.ErrorMessage);
	}

	/// <summary>
	/// 広告表示失敗の際に呼ばれます
	/// </summary>
	public void HandleDidFailToPlay(object sender, RewardedVideoErrorEventArgs e)
	{
		Debug.LogFormat("DebugLog class={0} method={1} groupId={2} unitId={3} errorCode={4} errorMessage={5}", this.GetType().Name, MethodBase.GetCurrentMethod().Name, e.GroupId, e.UnitId, e.ErrorCode, e.ErrorMessage);
	}  
}
```


## 各種イベント通知に関して

* イベントを設定することでPluginから広告のイベント通知を受け取ることが可能になります。
* イベントの設定の仕方に関しては、広告表示の実装例をご参照ください。



| イベント        | 通知タイミング       |
|-----------------|----------------------|
| OnDidLoad       | 広告読み込み完了の際   |
| OnWillAppear    | 広告画面表示直前     |
| OnDidAppear     | 広告画面表示直後     |
| OnWillDisappear | 広告画面を閉じる直前 |
| OnDidDisappear  | 広告画面を閉じた直後 |
| OnShouldReward  | リワード付与すべき際 |
| OnDidFailToLoad | 広告読み込み失敗の際 |
| OnDidFailToPlay | 広告表示失敗の際     |


## エラーコードについて

Errorは`OnDidFailToLoad`, `OnDidFailToPlay`のイベントから通知されます

| enum  | enum string            | 詳細情報                                                                                                                                |
|-------|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| -1000 | Timeout                | fluctのサーバへの広告リクエストがタイムアウトした時に通知されます。                                                                     |
| -1001 | InitializeFailed       | SDKの初期化が失敗した時に通知されます。                                                                                                 |
| -1002 | LoadFailed             | 広告読み込みが失敗した時に通知されます。                                                                                                |
| -1003 | NotReady               | 広告再生をコールしたが広告再生の準備が完了していない時に通知されます。                                                                  |
| -1004 | NoAds                  | 広告在庫がない場合に通知されます。                                                                                                      |
| -1005 | BadRequest             | 広告リクエスト時に指定するグループID, ユニットIDが適切でない時に通知されます。                                                          |
| -1006 | PlayFailed             | 広告再生開始時に広告再生に失敗した時に通知されます。                                                                                    |
| -1007 | WrongConfiguration     | FluctSDK-info.plistで全てのアドネットワークが広告配信停止設定になっているか、広告枠の設定に問題があり広告配信出来ない時に通知されます。 |
| -1008 | NotConnectedToInternet | 広告リクエスト時にインターネットに接続されていなかった場合に通知されます。                                                              |
| -1    | Unknown                | 上記以外のエラー時に通知されます。                                                                                                      |
