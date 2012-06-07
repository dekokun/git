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

1. ファイルを一元管理可能(リモートのリポジトリの概念)

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


