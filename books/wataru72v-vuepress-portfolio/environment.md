---
title: "STEP1: 環境構築"
---

# CloudShell をセットアップ

ハンズオンに入る前に Cloud Shell で開発環境を整えていきましょう。

[**GCP**](https://console.cloud.google.com/)のホーム画面に移動します。

- **Cloud Shell** のアイコンをクリック
- **新しいウィンドウで開く** をクリック

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/GCP_home.png?version=2)

- **エディタを開く** をクリック

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/GCP_cloudshell.png?version=2)

これで CloudShell の準備は完了です。
以降はこのコンソールとエディタを使って作業を行います。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/GCP_cloudshell_2.png)

# 作業用ディレクトリの用意

今回作業するディレクトリを作成します。
以下のコマンドをコンソールで実行してください。

```properties:~/
mkdir work
cd work
```

エディタでもワークスペースを変更しておきましょう。
この操作をしておかないと隠しファイルが表示されないなど、後に問題が出てきてしまいます。

- **File > Open Workspace** の順にクリック
- **work > Open** の順にクリック

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/openworkspace1.png)

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/openworkspace2.png)

ファイルツリーの **EXPLORER** の表示が **work** に変わり、ワークスペースが変更されます。

# 実行環境

本書作成時の各種バージョンは以下の通りです。

```properties
node --version
v10.14.2
npm --version
6.14.9
```

多少バージョンが異なっても問題ないかと思いますが、気になる方は揃えてください。
nvm が入っていますので、これでバージョンを変更します。

```properties
nvm install v10.14.2
nvm use v10.14.2
```
