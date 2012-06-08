バージョン管理システム
===

## バージョン管理システム

### 複数人もしくは一人での開発で困ること

* 皆が個々の好きな場所でファイルを作成しており、かき集めるのが大変…
* それぞれのファイルの最新の状態がわからないこのファイルの最新バージョンは誰が持っているのかな…
* 他の人の編集したソースを見るのが面倒(いちいち共有フォルダにおいてその場所を教えてあげなくちゃいけない！？！？)
* 皆のファイルを同じところで管理させようと共有ファイル上で開発させたらいつの間にか同じファイルを複数人で編集して上書きが発生。誰かの編集したものが消滅したっぽいがどれが消滅したのかよくわからない…
* ファイルを更新する際のバックアップのためにindex.html.20120611_1, index.html.20120611_2とか日付をつけてやってたけどファイルが増えすぎて鬱陶しいしどのファイルがどの変更の際のものかがわからない…
* この部分のコードがなんのために書かれているかわからない…
* この部分のコードは腐れ過ぎている誰が書いたんですか死んでくださいというかなんのためのコードかもわからないので質問したいです本当に誰が書いたんですか…

### 解決しよう！-> バージョン管理システム

#### 利点

1. ファイルを一元管理可能(中央のリポジトリの概念)
  * ファイルが散らばらない(かき集めるのが大変ではない)
  * 最新のファイルが簡単に手に入る
  * 簡単なバックアップになる
2. ソースコードの変更履歴を管理
  * このコードは誰がなんのために変更したのかという履歴を保持
  * 決まった時点へのソースコードの巻き戻しが可能
  * 日付付きバックアップを作成する必要などなく、気分がよい←人生において"精神衛生上よい"ことは非常に大切!!根性で解決しようとするな!
3. 同時に同じファイルを編集することが可能
  * 同じファイルを同時に編集しても編集内容が消えたりしない
  * 同時に複数人が編集したファイルの編集内容を可能な範囲で自動的に併合(マージ)してくれる

#### 欠点

1. 面倒(特に最初は)

IDEやエディタとの連携で面倒臭さを解消
今回は、バージョン管理の本質を教えるため、コマンドラインから実施

## 代表的なバージョン管理システム

* Git
  * 分散バージョン管理システム
  * 最近のオープンソースはもっぱらGit上で開発されている
  * 今回主に扱う

* SVN
  * 1時代前のバージョン管理システムの主流
  * 今回説明だけを行う

* Mercurial
  * Gitと同様、分散バージョン管理システム
  * Gitよりもわかりやすいようだが世間の流れはなぜかGit一辺倒。かわいそう(だが今回は主流のGitを扱います)

* CVS
  * 古い。SVNより更に1時代前のバージョン管理システム


## 用語解説(Git寄りの解説)

* コミット
  * ファイルの変更のスナップショットをとること。コミット時のソースコードや変更点は後ほど見ることが可能

* リポジトリ
  * データの格納場所。プロジェクトのコミット履歴の(ある程度)全てが入っている

* クローン(clone)
  * 別の場所のリポジトリから、ソースコードとプロジェクトの歴史を持ってくること

* プッシュ(push)
  * 手元のコミットの歴史をリモートのリポジトリに反映すること

* ブランチ
  * Gitの骨子。今回は教えないが、Gitで複数人開発するときに、ブランチを使うことができないと厳しいかもしれない
  * できることはできるが

## GitとSVNの比較

### Git

* オープンソースの主流(etc. PHP, heroku)
* リモートに接続できない状況でもバージョン管理可能
* ローカルにプロジェクトの全ての歴史が格納されている(分散バージョン管理システム)
  * 手元でコミットが可能
  * 気軽にコミットが可能
  * 手元でソース管理の歴史を見ることが可能であり、高速な動作が可能

### SVN

* 一昔前のオープンソースの主流(今でも結構使われているけれど)
* バージョン管理に関する作業を行うときは高頻度でリモートに接続する必要がある
* コミットすると全体に公開されるため、コミットに心理的抵抗
* SVNを使える技術者はかなり多い(と思う。多分)

## リポジトリの構成について(Gitの基本的な構成)

ホワイトボードに絵を描きながら説明

* ワークツリー
  * ローカルのソースコードそのもの

* index
  * これからコミットする差分の集合

* ローカルリポジトリ
  * これまでのプロジェクトの歴史とローカルでコミットした歴史の集合
  * ワークツリーの中にある.gitファイルに歴史が詰まってます

* 中央リポジトリ
  * 最終的にみんながローカルのコミットを反映する場所
  * 必須なものではないが、Gitを使用した基本的な開発では中央リポジトリが存在する

## 主な操作

* git status
  * 現在のワークツリーとindexの状態を表示

* git clone
  * 中央リポジトリからプロジェクトの歴史とソースコードを取得する

* git add
  * ワークツリーの変更をindexにあげる

* git commit
  * index上の差分をコミットする

* git push
  * コミットを中央リポジトリに反映する

* git pull
  * 他の人の中央リポジトリへの変更を自分のワークツリーに反映する

* コンフリクトによる編集
  * 他の人のコミットと自分のコミットが同じ箇所を編集していた場合、pullの際にコンフリクト(競合)が発生します
  * 解決してコミットしてあげましょう

* git commit --amend
  * 一つ前のコミットを取り消し、もう一度コミットします

* git reset
  * コミットを取り消すことができます
  * 使い方はググれ
  * 最初の頃は、一度したコミットを修正しようなどとは考えず、新しく修正するコミットをしたほうがいいのではないかと思わなくもない

## Githubアカウントを取ろう

### Githubとは

* 中央リポジトリを作成してくれるサイト
* オープンソースの開発も結構この上で行われている
* ソースコードの歴史などがWeb上で閲覧可能 例:https://github.com/dekokun/TDD/commits/master/test.js

### アカウント作成

* サインアップしよう https://github.com/
* Plans, Pricing and Signupボタンを押下して無料プランをどうぞ

