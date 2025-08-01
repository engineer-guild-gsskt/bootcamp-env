# 【Mac 版】環境構築

## はじめに

このマニュアルでは初回の講座を受けるにあたって最低限の環境構築の仕方を説明します。
よりリッチな環境を作りたい場合は[佐々木が普段使っている環境のマニュアル](https://github.com/philip82148/env-setup)があります。
どちらでセットアップしてもかまいませんし、後で移行することも可能です。

※佐々木のマニュアルでは VSCode の[Live Server](https://marketplace.cursorapi.com/items/?itemName=ritwickdey.LiveServer)という拡張機能のインストールについての記載がないため、[2. 拡張機能をインストールする](#2-拡張機能をインストールする)を参考に追加でインストールしてください。

環境構築は Git、VSCode が使えれば大丈夫です。それが出来れば、このマニュアルの通りにする必要はありません。

## 手順

### 1. VSCode をインストールする

#### 1. VSCode のインストール

[参考サイト](https://qiita.com/watamura/items/51c70fbb848e5f956fd6)の「1. VSCode のサイトにアクセス」~「6. アプリケーションフォルダから VSCode を開いてください」までを参考にインストールする。

#### 2. (Mac のみ)ターミナルから`code`コマンドで VSCode が起動できるようにする

[参考サイト](https://qiita.com/P-man_Brown/items/b18f31e3bb98b08ff31b)

> インストールした VSCode を開き、  
> [Command+Shift+P] -> "shell command"と入力 -> [Shell Command: Install 'code' command in PATH]を選択

### 2. (Windows のみ) WSL2 をインストールする

Mac ではこの手順はしなくてよい。

### 3. Git をインストールする

参考: [3.(Mac のみ)Git をインストールする](<https://github.com/philip82148/env-setup/blob/main/環境構築の手順/3.(Macのみ)Gitをインストールする.md>)

[参考サイト](https://prog-8.com/docs/git-env)を参考にインストールする。  
なお、現時点では「2. Git のインストール」まで出来ていればよく、ターミナル上で`git --version`を入力して [Enter] を押したときにバージョンが表示されれ(エラーが起こらなけれ)ばよい。

### 4. VSCode の設定をする

参考: [7.VSCode の設定をする](https://github.com/philip82148/env-setup/blob/main/環境構築の手順/7.VSCodeの設定をする.md)

#### 1. 拡張機能をインストールする

VSCode を開き、[公式サイト](https://learn.microsoft.com/ja-jp/power-pages/configure/vs-code-extension#install-visual-studio-code-extension)の「Visual Studio Code 拡張機能のインストール」の項を参考に、以下の拡張機能を検索窓で検索して全てインストールする。

- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) (コードフォーマッタ)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) (Git 情報を見やすくしてくれる)
- [Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory) (Git のログを見やすくしてくれる)
- [Live Server](https://marketplace.cursorapi.com/items/?itemName=ritwickdey.LiveServer) (HTML ページをプレビューする)

### 3. ファイル保存時に自動フォーマットするようにする

[参考サイト](https://zenn.dev/k_kazukiiiiii/articles/670ebae0005872)を参考に自動フォーマットの設定を行う。

> 1. VSCode 上で[Ctrl+,]/[Command+,] -> "Format On Save"と検索してチェックを入れる。
> 2. 続けて"Default Formatter"と検索して Prettier を選ぶ。
> 3. [Ctrl+Shift+P]/[Command+Shift+P]->[Reload Window]を選択。

### 5. Git の認証情報を設定する

参考: [8.Git の認証情報を設定する](https://github.com/philip82148/env-setup/blob/main/環境構築の手順/8.Gitの認証情報を設定する.md)

#### 1. GitHub のアカウントを作る

[参考サイト](https://yakiimosan.com/github-account-create/)を参考に[GitHub](https://github.co.jp/)のアカウントを作る。

#### 2. コマンドラインの Git にユーザー情報を設定する

[参考サイト](https://zenn.dev/sassan/articles/a1efb40422f2d7)

> ターミナルを開き、下記の 2 つを実行する。  
> ただし、ダブルクオーテーション内は自分で設定したいものにすること。  
> なお、これらはコミットログに記録され、外部に公開される。  
> どのようなものを設定すればいいかは参考サイトを参照。  
> また、個人メールを外部に公開したくない場合も参考サイトを参照。
>
> なお、ターミナルの開き方は[5.Python の環境構築をする](./5.Pythonの環境構築をする.md)等を参照。
> もちろん WSL 上で実行する。
>
> ```shell
> git config --global user.email "任意のメールアドレス"
> ```
>
> ```shell
> git config --global user.name "任意の名前"
> ```

#### 3. GitHub CLI をインストールする

最初に[参考サイト](https://qiita.com/zaburo/items/29fe23c1ceb6056109fd)を参考に Homebrew (アプリインストーラ) をインストールする。

> 下記をターミナルで実行する。画面の指示に従って[Enter]を押す。
>
> ```shell
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
> ```
>
> 場合によっては最後に、インストーラが`Run these two commands in your terminal to add Homebrew to your PATH:`と言ってくるので、その下の 2 行を実行する。  
> (ない場合は気にしなくてよい。)
>
> ```shell
> # これは例。実際に実行するのはインストーラが示したコマンドにすること。
> (echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/testuser/.zprofile
> eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
> ```

次にターミナルで下記を実行する。

```shell
brew install gh
```

#### 4. GitHub にログインする

[参考サイト](https://zenn.dev/sassan/articles/a1efb40422f2d7)  
※参考サイトは WSL での方法を説明しているが、Mac でも同じである。

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
> WSL では多分ブラウザは開かれないので直接 [https://github.com/login/device](https://github.com/login/device) を開く。  
> その後、コピーしたコードを張り付けて認証する。
>
> エラーが起こった時の対処法は[参考サイト](https://zenn.dev/sassan/articles/a1efb40422f2d7)を参照する。
