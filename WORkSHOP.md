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
![alt text](https://github.com/umiyosh/git/blob/master/img/ins001.jpg?raw=true)

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
  自分の名前と会社のメールアドレスを設定してください
  $ git config --global user.name "foo_bar"
  $ git config --global user.email "foo_bar@cybird.co.jp"
  $ git config -l
  →自分の名前とメールアドレスが表示されればOKです
  user.name=foo_bar
  user.email=foo_bar@cybird.co.jp
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

## 研修用資料

* [Title](https://github.com/umiyosh/git/blob/master/README.md)

