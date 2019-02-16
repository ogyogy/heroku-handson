# LINE Bot + Heroku
## 開発環境
### Must
- Git for Windows
- Heroku CLI
- LINE アカウント
- LINE Developers アカウント

### Option
- Visual Studio Code

## Gitリポジトリを作成

'''
$ git init
$ git add .
$ git commit -m "first commit"
'''

## Heroku環境にアプリを作成

<app name>は任意の名前、指定しない場合はランダムな名前でアプリが作成される

'''
$ heroku create <app name>
'''

## Heroku環境にリポジトリの内容をデプロイ

'''
$ git push heroku master
'''
