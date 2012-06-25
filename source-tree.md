# SourceTreeを使おう

## SourceTreeとは

* Mac用、GitのGUIクライアントだよ！

## インストール

* Mac App Storeで検索するか、以下ページからダウンロードしてみてね！
* [SourceTree](http://www.sourcetreeapp.com/)

## 使い方

1. 最初に起動すると多分こんな画面
  ![alt text](https://github.com/dekokun/git/blob/master/img/SourceTree01.png?raw=true)
  * ユーザ名、メールアドレスを入力しましょう(なんでもいいのですが、ここで登録した名前でコミットした人が記録されます。Githubアカウントと同じものを入れると無難ではないでしょうか)
1. 次は多分こんな画面
  ![alt text](https://github.com/dekokun/git/blob/master/img/SourceTree02.png?raw=true)
  * githubアカウントを入力してみてもいいのではないでしょうか
  * どう連携するのか、ちょっとまだ私はよくわかってない…
1. 次は多分こんな画面
  ![alt text](https://github.com/dekokun/git/blob/master/img/SourceTree03.png?raw=true)
  * ここで、自分のgitリポジトリがあるディレクトリ(.gitファイルが存在するディレクトリ)を選択しましょう
1. 次は多分こんな画面
  ![alt text](https://github.com/dekokun/git/blob/master/img/SourceTree04.png?raw=true)
  * 上記で登録したプロジェクトがあると思うので、そこでダブルクリックしましょう
1. 次は多分こんな画面
  ![alt text](https://github.com/dekokun/git/blob/master/img/SourceTree05.png?raw=true)
  * 左側にある"master"の部分をクリックするとログが見られますよ
  * ログ画面
    ![alt text](https://github.com/dekokun/git/blob/master/img/SourceTree06.png?raw=true)
  * コミットするときは上にある「コミット」を押します
  * コミット画面
    ![alt text](https://github.com/dekokun/git/blob/master/img/SourceTree07.png?raw=true)
    * 左下からファイルを選ぶと右下に差分が表示されるので、「ファイルをステージへ移動」を選択(これがgit addに相当)
    * その後、コミットメッセージを入力し「コミット」を押しましょう
    * 左下の「コミットを直ちにプッシュする」にチェックを入れておくと、コミットしたタイミングで自動的にgit pushが行われます

## 補足

* 上記、5分くらいだけSourceTreeを使ってみて書いた文章なので、間違いなどあるかもしれません。
* 間違いなどあったら、直してpull requestをくれるなりissueに上げるなりしていただけたらと思います
