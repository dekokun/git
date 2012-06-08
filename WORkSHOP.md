# VCS研修 WORKSHOP
## 環境構築
###  開発環境導入
#### 社外アクセス用のproxyの設定

パッケージマネージャなどが社外アクセスするため、社外アクセス用のProxyを設定します。ホワイトボードのコマンドを実行してください。

#### パッケージマネージャのインストール

  * homebrewインストール

```
$ /usr/bin/ruby -e "$(/usr/bin/curl -fksSL https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)"
```

  * xcodeインストール

  ホワイトボードのpathにあるdmgファイルを実行してインストールしてください。

  * Preferences-Download-Command Line Tools

  XCodeを開いて Preferences-Download-Command Line Toolsをダウンロード
![alt text](https://github.com/dekokun/git/blob/master/img/ins001.jpg?raw=true)

#### gitインストール

  * homebrewインストールした人

  ```
  $ sudo brew install git
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
  Enter file in which to save the key (/home/n99999/.ssh/id_rsa): →何も入力しないでEner
   Enter passphrase (empty for no passphrase): →何も入力しないでEner
   Enter same passphrase again:→何も入力しないでEner
   Your identification has been saved in /home/n99999/.ssh/id_rsa.
   Your public key has been saved in /home/n99999/.ssh/id_rsa.pub.
   The key fingerprint is:
   00:f0:81:06:d6:79:0d:13:9f:2b:b2:20:cd:a9:f4:fb n99999@yoshfront
   The key's randomart image is:
  ```

  以下コマンドにて公開鍵をクリップボードにコピーしておきてください。

  ```
  cat ~/.ssh/id_rsa.pub
  ```

  [GitHub](https://github.com/)にアクセスして、公開鍵を登録してください。
  1, 2, 3の順序で押下します。
  ![alt text](https://github.com/dekokun/git/blob/master/img/ins004.jpg?raw=true)
  以下のような画面が出るので、タイトルに任意の名称を入力し、公開鍵を登録してください。
  ![alt text](https://github.com/dekokun/git/blob/master/img/ins005.jpg?raw=true)

  <<課題リポジトリの登録をこちらで行います。休憩してください。>>

### 講義で覚えたコマンドのおさらい

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

## 研修用資料

* [Title](https://github.com/dekokun/git/blob/master/README.md)

