# LINE Bot + Heroku + GitHub
## Goal
- LINE Messaging APIでEcho Botを作成する

## 事前準備
### 開発環境
- 事前にインストールしておく
    - [Git for Windows](https://gitforwindows.org/)
    - [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
    - [Node.js](https://nodejs.org/ja/)
    - [Visual Studio Code](https://code.visualstudio.com/)

### アカウント
- 事前にアカウントを取得しておく
    - [GitHub](https://github.com/)
    - [LINE](https://entry-at.line.me/)
    - [LINE Developers](https://developers.line.biz/ja/)

## LINE Developersの初期設定
- [LineBot(MessageApi)を試してみる-heroku版](https://qiita.com/skycat_me/items/9f27cbd9354515df744a)
    - 基本的な準備の項目を参照してアカウント、チャンネル、アプリを作成する

## GitHub
### リポジトリの作成
- [GitHubアカウント作成とリポジトリの作成手順](https://qiita.com/kooohei/items/361da3c9dbb6e0c7946b)
    - リポジトリの作成の項目を参照

## Heroku
### Heroku環境作成
- [Heroku入門(Webアプリの作成とデプロイ)](https://webbibouroku.com/Blog/Article/heroku-getting-started)
    - Herokuアカウント登録とHeroku CLIのインストールを行う

### Heroku環境にアプリを作成

ターミナル上で以下のコマンドを実行

1. herokuにlogin

    - 初回のみ実行

```
$ heroku login
```

2. ユーザー名確認

    - 初回のみ実行、ユーザー名が正しく表示されていればログイン成功

```
$ heroku auth:whoami
```

3. アプリ作成

    - [app name]は任意の名前、指定しない場合はランダムな名前でアプリが作成される

```
$ heroku create [app name]
```

### Heroku+GitHubを連携して自動デプロイ

1. [HEROKU](https://jp.heroku.com/)の自身のアカウントにアクセス
2. Deploy → Automatic deploysからEnable Automatic Deploysを有効にする

### Herokuアプリの環境変数設定

1. 「Heroku環境にアプリを作成」で作成したアプリの設定を下記のように変更
    
    - Setting → Config Varsからアプリの環境変数を以下の表の通り設定

    |KEY|VALUE|
    |---|---|
    |CHANNEL_ACCESS_TOKEN|Access Token|
    |CHANNEL_SECRET|Channel Secret|

    - Access Token、Channel Secretの値は、[LINEDevelopersのアカウント](https://developers.line.biz/ja/)から作成したチャンネルの設定情報を入力

2. 以下のコマンドを入力して2.で設定した環境変数が正しく設定されていることを確認

```
$ heroku config
```

## GitHubリポジトリに実行ファイルをPush
1. [ogyogy/line-bot-echo](https://github.com/ogyogy/line-bot-echo)でDowwnload Zipを押下
2. 1.でダウンロードしたのZipを展開
3. 2.で展開したフォルダ内のすべてのファイルを連携したGitHubリポジトリにpush

## LINE Developersアカウントでの設定
1. 自身の[LINEDevelopersのアカウント](https://developers.line.biz/ja/)にアクセス
1. 今回作成したLINEチャンネルの設定情報にアクセス
1. Webhook URLに以下のURLを設定

```
https://Herokuアプリ名.herokuapp.com/callback
```

## 作成したアプリのテスト

- LINEのチャンネル設定上のQRコードでアプリ名を友達追加
- アプリを開き文字を送ると同じ文字が返ってくれば成功

## Heroku環境にリポジトリの内容をデプロイ

```
$ git push heroku master
```
