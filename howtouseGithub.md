# Github使い方運用ルール

基本は、プルリクは小さく、コミットは小さく！  
共同開発ではレビューアーの負担を下げることが重要です。


## リポジトリ



### ファイル無視

`.gitignore`で以下を無視してください。

```
./DS_Store
DS_Store
```

もしデザインデータが入っているなら
```
*.psd
*.ai
```
なども追加して無視してください。

### テンプレート
Issueと、pull requestのテンプレートを作ってあるので、  
(あとで作ります。)
まず、ルートディレクトリに`.github`というディレクトリを作成し
- `ISSUE_TEMPLATE.md`
- `PULL_REQUEST_TEMPLATE.md`
という名前のファイルを作成してください。

## ブランチ
なるべく小さい単位でブランチを切ってください。  
どんなに大きくなったとしても機能ごとです。
ブランチ名は以下のルールにしたがって命名してください。

```
YYYYMMDD_機能名
ex) 20180830_send_remind_mail
```


## プルリク
ブランチを切ったら最初にプルリクを出します。  
最初にプルリクを書くことで、やることがぶれないようにする。
これからどんな実装をしますよ、っていうのを他の人に示すイメージです。  
「それちょっと違うのでは……」みたいなフィードバックを実装前に得られるようにする。
何もコミットしていないとだせないので、以下のコマンドで、空コミットをしましょう。

```shell
$ git commit --allow-empty -m "make pull request"
```

### プルリクの名前
名前はなるべく具体的にしましょう。  

_良い例_  
- 〜のリファクタ
- 〜のバグ修正
- ユーザーログイン画面の作成
- ユーザーランクの機能追加

_悪い例_
- リファクタと機能追加
  - ２つ同時に行なっている
- 小松作業中
  - 何しているブランチかわからない
- slackbot開発
  - でかすぎる

### 接頭辞の使い方
プルリクには状況に応じて接頭辞をつけてください。

#### [WIP] タイトル
Work In Progress,開発中.  
これ最初につけます.  
ここで何か意見ある人は、気になったらコメントしてok.  

#### [IR] タイトル
In Review.
レビュー待ちの状態

#### タイトル（何も付けない）
マージ（リリース）待ちの状態。


## コミットにプレフィックスをつける
コミットのメッセージには`feat:`等プレフィックスをつけてください。  
コミットの範囲が明確になることでレビューがしやすくなり開発効率もアップします。
コミットは大きめに丁寧にコミットしましょう。  
あとでそのコミットを見て何をしたかがわかるように。  
もし以下のprefixが２つ付いてしまうようなコミットがあれば、それは大きすぎます。  
＊この中でどうしても使えなければ、自分でわかりやすいと思うprefixを作っても良いです。

- feat: A new feature
- fix: A bug fix
- docs: Documentation only changes
- style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- refactor: A code change that neither fixes a bug nor adds a feature
- perf: A code change that improves performance
- test: Adding missing or correcting existing tests
- chore: Changes to the build process or auxiliary tools and libraries such as documentation generation

## レビュー
レビュー依頼を出しましょう。
メンションつければok

### レビュー時のコメントについて
レビュアーはレビュー時にコメントにラベルをつけましょう。  
修正必須なのか、ただのアドバイスなのか。  
ただのアドバイスなのに、いちいち対応していたら開発スピードが落ちます。  
修正必須以外は対応するかの判断は実装者に委ねます。  

- [must]
  - 必ず対応して！修正必須。
- [imo]  
  - In My Opinion.自分の意見や提案・好み。 自分ならこう書くけどどうかな？というアドバイス。
- [nits]
  - nitspick,些細な指摘。 小さな指摘だけど出来れば直してほしい。インデントやタイポなど。
- [ask]  
  - 質問,確認。 コードの意味がわからない。ここ書いてないけどなんで変えた？テストした？
