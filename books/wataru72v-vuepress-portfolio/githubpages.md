---
title: "STEP7: GitHub Pages へデプロイ"
---

# ビルド

ビルドを行い GitHub Pages へのデプロイ素材を作成します。
この作業で今まで作成してきたポートフォリオを HTML へ変換します。

## 設定ファイルの編集

GitHub ではデプロイされたコードのうち、`docs/` に絞って GitHub Pages を適用できます。
GitHub Pages と同じリポジトリでソースを管理できるため便利です。
これを活用するため、ビルド後に以下のようなディレクトリ構成となるようにしておきます。

```sh
portfolio/
└── docs
    ├── 'docs' ------------- GitHub Pages として公開
    │    └── 'ビルド出力'
    ├── .npmignore
    ├── package.json
    └── src
        ├── about.md
        ├── service.md
        ├── product.md
        ├── sns.md
        ├── index.md
        └── .vuepress
```

[VuePress のドキュメントの GitHub Pages](https://vuepress.vuejs.org/guide/deploy.html#github-pages) を参考に以下のように設定ファイルを編集します。

```diff:~/work/portfolio/docs/src/.vuepress/config.js(抜粋)
module.exports = {
  title: "Wataru Docs",
  description: description,
+ dest: 'docs/',
+ base: '/portfolio/',
```

- dest
  ビルドの出力先となるディレクトリを指定しています。

- base
  GitHub Pages では`https://ユーザーID.github.io/リポジトリ名/`という URL が与えられます。
  そのため URL のパスを合わせるために `base` に `/リポジトリ名/` を設定する必要があります。
  ここでは `/portfolio/` としています。

## ビルド実行

ビルドを実行します。
以下のコマンドを入力してください。

```properties:~/work/portfolio/docs/
npm run build
```

ビルド終わると `docs` というディレクトリが出現します。
この中に各ページが HTML への変換されたものが格納されています。

# GitHub にリポジトリを作成

[GitHub](https://github.com/) 上にデプロイとなるリポジトリを作成します。
以下の手順を実行して下さい。

- [GitHub](https://github.com/) へ移動
- **Repositories** の **New** をクリック
- **Repository name** にリポジトリ名を入力
  - ここでは `portfolio` と入力
- **Public** を選択
- **Create repository** をクリック

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/github1.png?version=1)

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/github2.png?version=1)

これでリポジトリの準備は完了です。

# コードを GitHub へ Push

GitHub 上の **…or create a new repository on the command line** を参考に `push` を行います。
以下コマンドを実行してください。

:::messages
`push` 実行後にユーザー ID とパスワード解答する必要があります。
:::

```properties:~/work/portfolio/docs/
echo "# portfolio" >> README.md
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/wataru72v/portfolio.git
git push -u origin main
```

これで GitHub への `push` は完了です。
作成したリポジトリのページを更新するとコードが見えるようになっています。

# GitHub Pages の公開

GitHub Pages を使ってポートフォリオを公開します。
以下の手順を実行してください。

- **Settings** をクリック
- **GitHub Pages** の設定を変更
  - Branch: `main`
  - Folder: `/docs`
- **Save** をクリック

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/githubpages1.png?version=1)

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/githubpages2.png?version=1)

これで GitHub Pages の設定は完了です。
`https://ユーザーID.github.io/リポジトリ名/`という URL でポートフォリオが公開されています。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/githubpages3.png?version=1)
