# バージョン管理システム研修 WORKSHOP
## git環境構築
### 社外アクセス用のproxyの設定

パッケージマネージャなどが社外アクセスするため、社外アクセス用のProxyを設定します。
ホワイトボードurlにアクセスしwikiに書いてあるproxy設定のコマンドを各自のターミナルで実行してください。

### パッケージマネージャのインストール

  * homebrewインストール

```
$ /usr/bin/ruby -e "$(/usr/bin/curl -fksSL https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)"
```

  * xcodeインストール

  ホワイトボードのpathにあるdmgファイルを実行してインストールしてください。

  * Preferences-Download-Command Line Tools

  XCodeを開いて Preferences-Download-Command Line Toolsをダウンロード
![alt text](https://github.com/dekokun/git/blob/master/img/ins001.jpg?raw=true)

### gitインストール

  * homebrewインストールした人

  ```
  $ brew install git
  ```

  **こんなの出た人がいたら、呼んでください その1**

  ```
  Cowardly refusing to sudo brew
  ```

  /usr/localのパーミッションが怪しい
  > 対処:
  > <code>$ sudo chown -R root /usr/local</code>

  **こんなの出た人がいたら、呼んでください その2**

  ```
  giomime.c:68:10: fatal error: '/Developer/Headers/FlatCarbon/Files.h' file not found
  #include </Developer/Headers/FlatCarbon/Files.h>
           ^
  1 error generated.
  make[1]: *** [giomime.lo] Error 1
  $ /usr/bin/ruby -e "$(/usr/bin/curl -fsSL https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)"
  ````

  > 対処:
  > <code>$ sudo ln -s /Applications/Xcode.app/Contents/Developer /Developer</code>

  * MacPortsを使っている人

  ```
  $ sudo port install git-core +gitweb +svn
  ```

  * gitコンフィグの設定(自分の名前とメアドの設定)

  ```
  自分の名前と会社のメールアドレスを設定してください。FQDNはうちのドメイン名です。
  $ git config --global user.name "foo_bar"
  $ git config --global user.email "foo_bar@FQDN"
  $ git config -l
  →自分の名前とメールアドレスが表示されればOKです
  user.name=foo_bar
  user.email=foo_bar@FQDN
  ```

  * credential-osxkeychain の設定

  以下のコマンドを入力してusageが返ってくるか試してください

  ```
  $ git credential-osxkeychain
  # Usage: git credential-osxkeychain <get|store|erase>
  ```

  ※ 出なかった場合はブラウザから以下をDownload後、ターミナルから次のコマンドを打ってください
  http://github-media-downloads.s3.amazonaws.com/osx/git-credential-osxkeychain

  ```
  $ mv ~/Downloads/git-credential-osxkeychain /usr/local/bin/
  $ chmod +x /usr/local/bin/git-credential-osxkeychain
  ```

  credential-osxkeychain導入後 git configにosxkeychainの設定を行なってださい。

  ```
  $ git config --global credential.helper osxkeychain
  $ git config -l
  →以下が表示に含まれていればOKです
  credential.helper=osxkeychain
  ```

  * GitHubアカウント作成

  [GitHub](https://github.com/)にアクセスして、アカウントを作成します。

  トップページから<code>Signup and Pricing</code>を押下し、<code>Create a free account</code>を選びます
  ![alt text](https://github.com/dekokun/git/blob/master/img/ins002.jpg?raw=true)

  事前にgit configで設定したuser名とメールアドレスを入力しｔアカウントを作成します
  ![alt text](https://github.com/dekokun/git/blob/master/img/ins003.jpg?raw=true)

  * 鍵の作成と登録

  Macにて鍵を作成します。
  パスフレーズを聞かれますが、何も入れずに公開鍵を生成してください。

  ```
  $ ssh-keygen -t rsa
  Generating public/private rsa key pair.
  Enter file in which to save the key (/home/n99999/.ssh/id_rsa): →何も入力しないでEnter
   Enter passphrase (empty for no passphrase): →何も入力しないでEnter
   Enter same passphrase again:→何も入力しないでEnter
   Your identification has been saved in /home/n99999/.ssh/id_rsa.
   Your public key has been saved in /home/n99999/.ssh/id_rsa.pub.
   The key fingerprint is:
   xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx n99999@xxxxxxxxx
   The key's randomart image is:
  ```

  以下コマンドにて公開鍵をクリップボードにコピーしておいてください。

  ```
  cat ~/.ssh/id_rsa.pub
  ```

  [GitHub](https://github.com/)にアクセスして、公開鍵を登録してください。
  1, 2, 3の順序で押下します。
  ![alt text](https://github.com/dekokun/git/blob/master/img/ins004.jpg?raw=true)
  以下のような画面が出るので、タイトルに任意の名称を入力し、公開鍵を登録してください。
  ![alt text](https://github.com/dekokun/git/blob/master/img/ins005.jpg?raw=true)

  <<課題リポジトリの登録をこちらで行います。休憩してください。>>

## 講義で覚えたコマンドのおさらい

  * GitHubアカウントで課題リポジトリを、見てみよう。

  [GitHub](https://github.com/)にアクセスして、自分のリポジトリを確認してください。
  以下からリポジトリ、にアクセスできます。
  ![alt text](https://github.com/dekokun/git/blob/master/img/rev001.jpg?raw=true)

  リポジトリの画面の簡単な説明。
  ![alt text](https://github.com/dekokun/git/blob/master/img/rev002.jpg?raw=true)
  他にもいろいろ、ありますがいまのところこれだけ覚えてください。

  * チームリポジトリをcloneしてみよう

  ターミナルから以下コマンドを実行して、ローカルにcloneしてください。

  ```
  $ cd 作業ディレクトリ
  $ git clone https://github.com/dekokun/trainingA.git
  $ ls -la trainingA
  $ cd trainingA
  ```

  * 編集してcommitしてみよう:ステージ編

  READMEを任意の内容で各自編集してください。１行適当なコメントを書くだけで良いです。
  <code>git status</code> を打ってみてください。未commitのファイルが表示されます。
  <code>Changes not staged for commit:</code>と表示されます。
  ```
  # On branch master
  # Changes not staged for commit:
  #   (use "git add <file>..." to update what will be committed)
  #   (use "git checkout -- <file>..." to discard changes in working directory)
  #
  #       modified:   WORkSHOP.md
  #
  no changes added to commit (use "git add" and/or "git commit -a")
  ```

  差分を見たいときは<code>git diff</code>を打ってください。ワークツリーと先頭commitとの差分が表示されます。

  ```
  diff --git a/README b/README
  index 2262de0..e42f4ce 100644
  --- a/README
  +++ b/README
  @@ -1 +1,2 @@
   hoge
  +fuga
  ```

  +が追加された行です。
  -が削除された行です。

  <code>git add <FILE名></code>でindexにステージします。
  <code>git status</code>を打ってみてください。<code>Changes to be committed:</code>という表示に変わっています。
  この状態でローカルにcommit可能となります。

  ```
  # On branch master
  # Changes to be committed:
  #   (use "git reset HEAD <file>..." to unstage)
  #
  #       modified:   README
  #
  ```

  また、ステージされたファイルと先頭commitの差分を見る場合は<code>git diff --cached</code>と打ってください。
  なお、間違えてgit add してしまった場合は上記に表示されているように<code>git reset HEAD <file>...</code>で
  アンステージできます。

  * 編集してcommitしてみよう:コミット

  <code>git commit</code>でcommitできます。
  ```
  $ git commit -m 'XXXXのための変更'
  [master 5e0cf17] XXXXのための変更
   1 files changed, 1 insertions(+), 0 deletions(-)
  ```

  <code>git log</code>でcommitログが参照できます。

  ```
  $ git log
  commit 5e0cf179549dc74a92bba65cca7b432b0c07beaf
  Author: foo_bar <foo_bar@FQDN>
  Date:   Fri Jun 8 17:30:33 2012 +0900

      XXXXのための変更

  commit 1be8836ad569d99a543f44d4ee589a51d58d3f20
  Author: foo_bar <foo_bar@FQDN>
  Date:   Fri Jun 8 17:15:15 2012 +0900

      initial commit
  ```

  * リモートにpushしてみよう

  リモートの変更を取り込んで<code>git pull origin master</code>, 自分の変更をリモートに反映<code>git push origin master</code>します。
  チームメンバー４人の<code>git push origin master</code>する順番を決めてください。
  リモートに変更が無いので、一人目のpushはなにもおこらず、うまくいくはずです。

  ```
  $  git pull origin master
  From https://github.com/dekokun/trainingA.git
   * branch            master     -> FETCH_HEAD
  Already up-to-date.
  $  git push origin master
  To https://github.com/dekokun/trainingA.git
     1be8836..5e0cf17 master -> master
  ```

  チームメンバーの人が同じ行を編集しているので必ずコンフリクトします。
  二人目以降からはコンフリクトを解決しましょう。以下のように機械的に解決できないCONFLICTが起きたよとgitが言ってます。

  ```
  $  git pull origin master
  remote: Counting objects: 5, done.
  remote: Compressing objects: 100% (2/2), done.
  remote: Total 3 (delta 1), reused 3 (delta 1)
  Unpacking objects: 100% (3/3), done.
  From github.com:umiyosh/git
   * branch            master     -> FETCH_HEAD
  Auto-merging WORkSHOP.md
  CONFLICT (content): Merge conflict in README
  Automatic merge failed; fix conflicts and then commit the result.
  ```
  READMEの中身はコンフリクトした行に<code><<<<<<< HEAD</code>、 <code>=======</code>,  <code>>>>>>>> COMMITID</code>
  のようなマーカーが保存されてます。具体的には以下のようになっています。

  ```
  <<<<<<< HEAD
  なんらかの編集行01
  なんらかの編集行01
  =======
  なんらかの編集行02
  なんらかの編集行02
  なんらかの編集行02
  >>>>>>> 224ba17dc5e2b24417ed675bd4a52381b93dede6
  ```

  この中から残したい行を残し(あるいは両方残し)、マーカーの部分を削除して保存してください。
  保存後に<code>git status</code>を打つと以下のように表示されます。

  ````
  # On branch umiwk
  # Unmerged paths:
  #   (use "git add/rm <file>..." as appropriate to mark resolution)
  #
  #       both modified:      README
  #
  no changes added to commit (use "git add" and/or "git commit -a")
  ```

  表示されてるように<code>git add <FILE名></code>と打てばChange to be commitedになります。
  そのまま<code>git commit</code>。エディタが起動してマージcommitログを刻めます。

  ```
  1 Merge branch 'master' of github.com:umiyosh/git into umiwk
  2
  3 Conflicts:
  4 >README
  5 #
  6 # It looks like you may be committing a merge.
  7 # If this is not correct, please remove the file
  8 #>.git/MERGE_HEAD
  9 # and try again.
  ```

  マージが完了したら、<code>git push origin master</code>して中央リポジトリに変更を反映してください。

## グループワーク
  チームリポジトリで共同作業を体験しましょう。
  以下のテーマで各自READMEファイル, およびQUESTIONファイルを編集して、最終的に発表してもらいます。
  フォーマットは、テキスト形式で作成してください。

  * 自分の自己紹介をREADMEに書き加えてください
    1. 名前
    2. 興味のあること。趣味なり技術ネタなり
    3. 本日学習したことの感想
    4. 今後の抱負
  * 上記はチームメンバーが自分の文を編集してcommitしてください
  * 上記に加えてQUESTIONファイル(1ファイルにしてください)を新規作成し、チームメンバー各自が抱いたgitの疑問点をQUESTIONファイルに書き加えてください。

  * 作成したアウトプットは以下の形式で発表します
    1. 自分の担当分についてはチームメンバ各自で発表します。(持ち時間:1分/一人)
    2. QUESTIONは講師側で読み上げて回答します

  各自でコンフリクトがおきたさいは解決して中央リポジトリに反映を行い共同作業を行なってください。

  * 余力があるチームへ

   余力があるチームは[ markdown ](http://blog.2310.net/archives/6)を使い、シンプルでリッチなREADME, QUESTIONを作成してくみてください。

  * さらに余力があるハカー的なチームへ

  [ OneMoreThing ](https://github.com/dekokun/git/blob/master/one-more-thing.md)に記載されているTDDベースのcommit作業を行なってみてください。バグを混入させないようcommitを刻むといった, Gitの正しい使い方が理解できます。

## より深めたい人へ
 Pro Git(無料のPDF)は読みやすく、深めることができるので興味があるひとは読んで見ることをおすすめします！
* [Pro Git](https://docs.google.com/file/d/0BxkaLAGEeWgLNDRhYzQ3MDgtNmQ1NC00ODZiLThmYzYtYmJlYWE5YzY2Mjkw/edit?hl=en&pli=1)

