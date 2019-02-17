# LINE Bot + Heroku (+ GitHub)
## 開発環境
### Must
- [Git for Windows](https://gitforwindows.org/)
- [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
- [LINE アカウント](https://entry-at.line.me/)
- [LINE Developers アカウント](https://developers.line.biz/ja/)
- [GitHub アカウント](https://github.com/)
### Option
- [Visual Studio Code](https://code.visualstudio.com/)

## Visual Studio Code (Option)
- 必須ではないが，推奨
- 設定方法
    - ???

## LINE Developersのアカウント／チャンネル／アプリの作成
- 下記参考文献の「基本的な準備」までを行うこと
- [LineBot(MessageApi)を試してみる-heroku版](https://qiita.com/skycat_me/items/9f27cbd9354515df744a)

## Gitリポジトリを作成（HerokuとGitHubとの連携を行う場合，この作業は必要なし）

```
$ git init
$ git add .
$ git commit -m "first commit"
```

## GitHub
### GitHub環境作成
- 下記参考文献のリポジトリの作成まで行うこと
    - [GitHubアカウント作成とリポジトリの作成手順](https://qiita.com/kooohei/items/361da3c9dbb6e0c7946b)

## Heroku
### Heroku環境作成
- 下記参考文献中の「Herokuアカウント登録」「Heroku CLIのインストール」まで行うこと
    - [Heroku入門(Webアプリの作成とデプロイ)](https://webbibouroku.com/Blog/Article/heroku-getting-started)

### Heroku環境にアプリを作成（Visual Studio Codeのbashで行うことを推奨）
1. herokuにlogin
```
heroku login
```
1. ユーザー名確認（やらなくても良い）
```
heroku auth:whoami
```
1. アプリ作成
    - [app name]は任意の名前、指定しない場合はランダムな名前でアプリが作成される
```
$ heroku create [app name]
```

### GitHubとの連携
1. [HEROKU](https://jp.heroku.com/)の自身のアカウントにアクセス
1. 「Heroku環境にアプリを作成」で作成したアプリの設定を下記のように変更
    - Deployタブ → Automatic deploys項目 → Enable Automatic Deploysをクリック
    - Settingタブ → Config Vars項目
    |KEY|VALUE|
    |---|---|
    |CHANNEL_ACCESS_TOKEN|[アクセストークン]|
    |---|---|
    |CHANNEL_SECRET|[Channel Secret]|
        - [アクセストークン], [Channel Secret]の値は，自身の[LINEDevelopersのアカウント](https://developers.line.biz/ja/)のチャンネルの設定情報から取得すること
1. VSCodeに戻り，上記の環境変数が設定されていることを確認
```
heroku config
```

## GitHubの今回作成したレポジトリに必要なソースをプッシュ
1. [echo-bot](https://github.com/yukie7/echo-bot.git)でDowwnload Zipを押下
1. ローカルにダウンロードされた1.のファイル群を展開
1. 展開されたファイル群があるディレクトリをVSodeで開く
1. すべてのファイルを今回GitHubで作成したレポジトリにpush（作成途中）
```
git init
...
```

## LINE Developersアカウントでの設定
1. 自身の[LINEDevelopersのアカウント](https://developers.line.biz/ja/)にアクセス
1. 今回作成したチャンネルの設定情報にアクセス
1. Webhook URLに下記のURLを入力
    - [Heroku URL] + callback
        - [Heroku URL] = Herokuの今回作成したページ → Settingタブ → Domains and certificates項目に書かれていURL

## テスト
    - LINEのチャンネル設定上のQRコードでアプリ名を友達追加
    - その友達に対して，文字を送ると，同じ文字が返ってくる（echo botの完成）

## Heroku環境にリポジトリの内容をデプロイ

```
$ git push heroku master
```
