# 【Windows 版】環境構築

## はじめに

このマニュアルでは初回の講座を受けるにあたって最低限の環境構築の仕方を説明します。
よりリッチな環境を作りたい場合は[佐々木が普段使っている環境のマニュアル](https://github.com/philip82148/env-setup)があります。
どちらでセットアップしてもかまいませんし、後で移行することも可能です。

※佐々木のマニュアルでは VSCode の[Live Server](https://marketplace.cursorapi.com/items/?itemName=ritwickdey.LiveServer)という拡張機能のインストールについての記載がないため、[2. 拡張機能をインストールする](#2-拡張機能をインストールする)を参考に追加でインストールしてください。

環境構築は WSL 上で Git、VSCode が使えれば大丈夫です。それが出来れば、このマニュアルの通りにする必要はありません。

## 手順

### 1. VSCode をインストールする

参考: [1.VSCode をインストールする](https://github.com/philip82148/env-setup/blob/main/環境構築の手順/1.VSCodeをインストールする.md)

[参考サイト](https://www.javadrive.jp/vscode/install/index1.html)の「Visual Studio Code をダウンロードする」と「Visual Studio Code をインストールする」の項を参考にインストールする。

### 2. WSL2 をインストールする

参考: [2.(Windows のみ)WSL2 をインストールする](<https://github.com/philip82148/env-setup/blob/main/環境構築の手順/2.(Windowsのみ)WSL2をインストールする.md>)

#### 1. ターミナルを開く

[参考サイト](https://kb.seeck.jp/archives/20593)

> [スタート] -> [すべてのアプリ] –> [ターミナル]をクリック

#### 2. WSL2 をインストールする

[参考サイト](https://learn.microsoft.com/ja-jp/windows/wsl/install)

> 1. 以下をターミナルに打ち込んで [Enter]。  
>    いくつかインストールしてよいかを聞くダイアログが開くので「はい」をクリック。
>    インストールは数分かかる。
>
> ```shell
> wsl --install -d Ubuntu-22.04
> ```
>
> 2. その後、一旦パソコンを再起動する。
>
> 3. 再起動後、自動的にターミナルが開かれ、ユーザーネームとパスワードを聞かれるので任意のユーザー名とパスワードを設定する。  
>    これは、Windows の中に Linux (正確には Ubuntu-22.04) という全く別の OS を作ったために、Linux 用のアカウントの作成を求められているということである。  
>    ユーザー名は Windows のものと同じでもよいが、パスワードは頻繁に使うので覚えやすいものが良い。  
>    (自動的にターミナルが開かれなかった場合は検索窓で`Ubuntu-22.04`を検索して開く。)
>
> 4. パスワードを設定したら、以下のような表示が出るまで待つ。
>
> ```shell
> アカウント名@パソコン名:~$
> ```

#### 3. パッケージリストの更新とアップグレードを行う

> 0. 下記の「正しい方」がターミナルに表示されていることを確認する。  
>    間違っている方が表示されている場合は、Linux ではなく Windows のシェルになっている。  
>    `wsl`とターミナルに打ち込んで [Enter] をすると Linux のシェルに切り替わる。
>
> ```shell
> # 正しい方
> アカウント名@パソコン名:~$
>
> # 間違っている方
> PS C:\Users\Windowsのユーザー名>
>
> # 間違っていた場合下記を実行
> wsl
> ```
>
> 1. パッケージリストの更新とアップグレードを行う
>
> ```shell
> sudo apt -y update
> sudo apt -y upgrade
> ```

### 3. (Mac のみ) Git をインストールする

Windows ではこの手順はしなくてよい。

### 4. VSCode の設定をする

参考: [7.VSCode の設定をする](https://github.com/philip82148/env-setup/blob/main/環境構築の手順/7.VSCodeの設定をする.md)

#### 1. VSCode を起動する

**WSL 上で確実に開くために、ターミナルの WSL 上で以下を実行する**。

```shell
code ~
```

ここで、**VSCode の左下の緑の部分に`WSL: Ubuntu-22.04`と表示されていることを確認する**。  
**なお、今後 VSCode を開くときは毎回左下の緑の部分が`WSL: Ubuntu-22.04`と表示されている(VSCode が WSL とつながっている)ことを確認すること。**  
とはいえ、普通に起動してもこの状態になることがあるので、毎回この方法で起動する必要はない。

なっていない場合は、以下の手順を実行する。

1. [2. 拡張機能をインストールする](#2-拡張機能をインストールする)の項で説明している方法で、[WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)という拡張機能をインストールする。
2. VSCode の再起動を促されるので、再起動する。促されない場合は手動で[Ctrl+Shift+P]->[Reload Window]を選択して再起動する。
3. VSCode の左下の緑の部分をクリックし、[Connect to WSL]を選択する。

#### 2. 拡張機能をインストールする

[公式サイト](https://learn.microsoft.com/ja-jp/power-pages/configure/vs-code-extension#install-visual-studio-code-extension)の「Visual Studio Code 拡張機能のインストール」の項を参考に、以下の拡張機能を検索窓で検索して全てインストールする。

- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) (コードフォーマッタ)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) (Git 情報を見やすくしてくれる)
- [Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory) (Git のログを見やすくしてくれる)
- [Live Server](https://marketplace.cursorapi.com/items/?itemName=ritwickdey.LiveServer) (HTML ページをプレビューする)

#### 3. ファイル保存時に自動フォーマットするようにする

[参考サイト](https://zenn.dev/k_kazukiiiiii/articles/670ebae0005872)を参考に自動フォーマットの設定を行う。

> 1. VSCode 上で[Ctrl+,] -> "Format On Save"と検索してチェックを入れる。
> 2. 続けて"Default Formatter"と検索して Prettier を選ぶ。
> 3. [Ctrl+Shift+P] -> [Reload Window]を選択。

### 5. Git の認証情報を設定する

参考: [8.Git の認証情報を設定する](https://github.com/philip82148/env-setup/blob/main/環境構築の手順/8.Gitの認証情報を設定する.md)

#### 1. GitHub のアカウントを作る

[参考サイト](https://yakiimosan.com/github-account-create/)を参考に[GitHub](https://github.co.jp/)のアカウントを作る。

#### 2. コマンドラインの Git にユーザー情報を設定する

[参考サイト](https://zenn.dev/sassan/articles/a1efb40422f2d7)

> 以下の 2 つをターミナルで実行する。日本語の部分は書き換えること。  
> **これらは外部に公開される。** それが嫌な場合は任意のメールと名前を設定してよい。  
> メールに関しては GitHub 側が用意したダミーメールを使うこともできる。  
> 詳しくは参考サイトを参照。
>
> ```shell
> git config --global user.email "GitHubアカウントのメールアドレス"
> ```
>
> ```shell
> git config --global user.name "GitHubアカウントのID"
> ```

#### 3. GitHub CLI をインストールする

[参考サイト](https://zenn.dev/sassan/articles/a1efb40422f2d7)

> 以下をターミナルで実行する。
>
> ```shell
> sudo apt -y install gh
> ```

#### 4. GitHub にログインする

[参考サイト](https://zenn.dev/sassan/articles/a1efb40422f2d7)

> 以下をターミナルで実行する。
>
> ```shell
> gh auth login
> ```
>
> 質問には以下のように答える。
>
> ```console
> What account do you want to log into?
>  -> GitHub.com
> What is your preferred protocol for Git operations?
>  -> HTTPS
> Authenticate Git with your GitHub credentials?
>  -> Y
> How would you like to authenticate GitHub CLI?
>  -> Login with a web browser
> First copy your one-time code: XXXX-XXXX
>  -> XXXX-XXXXの部分をコピーする
> Press Enter to open github.com in your browser...
> ```
>
> この後 [Enter] を押す。  
> ブラウザが自動で開かれるはずだが、開かなかったら直接 [https://github.com/login/device](https://github.com/login/device) を開く。  
> その後、コピーしたコードを張り付けて認証する。
>
> エラーが起こった時の対処法は[参考サイト](https://zenn.dev/sassan/articles/a1efb40422f2d7)を参照する。
