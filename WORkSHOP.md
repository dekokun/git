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
  * Preferences-Download-Command Line Tools

  XCodeを開いて Preferences-Download-Command Line Toolsをダウンロード

#### gitインストール

  * homebrewインストールした人

  ```
  $ brew install git
  ```

  ``` こんなの出た人がいたら、呼んでください
  Cowardly refusing to sudo brew
  ```

> 原因:/usr/localのパーミッションが怪しい
> 対処:
> <code>$ sudo chown -R root /usr/local</code>

  ``` こんなの出た人がいたら、呼んでください
  giomime.c:68:10: fatal error: '/Developer/Headers/FlatCarbon/Files.h' file not found
  #include </Developer/Headers/FlatCarbon/Files.h>
           ^
  1 error generated.
  make[1]: *** [giomime.lo] Error 1
  $ /usr/bin/ruby -e "$(/usr/bin/curl -fsSL https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)"
  ````

> 対処:
> $ sudo ln -s /Applications/Xcode.app/Contents/Developer /Developer

  * MacPortsを使っている人

  ```
  $ port install git
  ```

## 研修用資料

* [Title](https://github.com/umiyosh/git/blob/master/README.md)

