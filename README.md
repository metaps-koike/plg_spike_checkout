plg_spike_checkout
====

[EC-CUBE](http://www.ec-cube.net)用のプラグインです。
このプラグインをEC-CUBEにインストールすることにより、[SPIKE](https://spike.cc)の決済機能を利用出来ます。


## 機能概要

- [SPIKE Checkout](https://spike.cc/dashboard/developer/docs/references#a1)を用いた決済を提供します。
- 受注管理にて決済のキャンセルが可能です。
- 管理画面にてゲスト決済のオプションを設定できます。
- [Webhook](https://spike.cc/dashboard/developer/docs/references#a4)の受信は未対応です。
  - SPIKEからの状態変更を自動でEC-CUBEへ反映できません。
- SPIKEでアカウント登録することにより、テスト（サンドボックス）環境の利用を行えます。
  - 本番環境での決済を行うためには[ビジネスプレミアム](https://spike.cc/#pricing)への登録が必要になります。


## システム要件

- EC-CUBE
  - 2.13.*
  - 2.12.*
- PHP
  - 5.3.*
  - 5.4.*
  - 5.5.*
  - REST APIの呼び出しにはHTTPSを使用します。PHPにてHTTPSでの通信ができることが必須です。
- 対応端末
  - o PC、スマートフォン
  - x フィーチャーフォン
    - SPIKE CheckoutがPC,スマートフォンブラウザでの動作を前提として構築されているためです。


## 動作保証

SPIKE開発チームが動作検証を行い、正常動作を確認したバージョンはこちらになります。

- 2.13系
  - 2.13.2
- 2.12系
 - 2.12.6


ただし、他の決済モジュールやプラグインと併用した場合の動作検証はおこなっていません。


## 導入手順

### SPIKEでのアカウント登録

- [SPIKE](https://spike.cc/)にてアカウントを作成します。
- SPIKE Checkoutを本番環境にて利用する場合、SPIKEにてビジネスプレミアムへの申し込みが必要です。
  - サンドボックス環境の利用はSPIKEへの登録のみで利用可能です。

### EC-CUBEへのプラグイン登録

- 最新の安定バージョン [plg_spike_checkout-master.tar.gz](https://download.spike.cc/ec-cube/plg_spike_checkout-master.tar.gz)をダウンロードします。
- EC-CUBEの管理画面よりプラグインの登録をおこないます。
  - 「オーナーズストアメニュー」 → 「プラグイン管理」 → 「プラグイン管理」ページを表示します。
  -  最初にダウンロードしたファイルをアップロードしてインストールボタンを押します。
- インストールが成功すると、プラグイン一覧にSPIKE Checkoutが表示されるので、「プラグイン設定」リンクを開きます。
- [SPIKEの開発ダッシュボード](https://spike.cc/dashboard/developer/api)から取得したAPIキーを登録します。
- プラグイン一覧にて、「有効」チェックボックスにチェックを入れて有効化します。
- 以上の設定により、SPIKEのクレジットカード決済が支払方法として選択可能となります。

### 配送方法の設定

配送手段に対して、SPIKEによる決済を選択出来るように関連づけを設定します。

- EC-CUBE管理画面の「基本情報管理」→「配送方法設定」 メニューを選び、配送方法の一覧を表示します。
- 使用する配送業者の「編集」を押して、設定画面を表示します。
- 取扱支払方法の「SPIKEクレジットカード決済」をチェックします。


### 支払方法の設定

任意の設定項目です。必要に応じて、SPIKE決済の設定を変更出来ます。

- EC-CUBE管理画面の「基本情報管理」→「支払方法設定」 メニューを選び、支払方法の一覧を表示します。
- SPIKE決済のレコードにある「編集」を押して、設定画面を表示します。
- 決済下限金額や、上限金額などを設定出来ます。


## 開発者向け

### プラグインの作成

各自でプラグインファイルを圧縮して作成する場合に注意が必要です。

EC-CUBEのプラグインはディレクトリを含んで圧縮されていると、正常にインストール出来ません。
そのためディレクトリを含まない形で圧縮します。


実行例：
```
% git clone git@github.com:metaps/plg_spike_checkout.git
% cd plg_spike_checkout
% tar cvzf ../plg_spike_checkout.tar.gz *
```


### バグ修正や機能追加

Issuesへの登録、またはPull Requestをお願いします。


## ライセンス

- [GPL v3](http://www.gnu.org/licenses/gpl.html)
