---
title: "STEP2: VuePressの導入"
---

# VuePress プロジェクトを作成する

[VuePress のドキュメントの Quick Start](https://vuepress.vuejs.org/guide/getting-started.html#quick-start)を参考にプロジェクトを作成します。

以下のコマンドをコンソールで実行してください。
プロジェクト名など色々と質問されますが、全て Enter で大丈夫です。

```properties:~/
npx create-vuepress-site portfolio
```

質問に答えてしばらく待つと portfolio ディレクトリが作成されます。
ディレクト構成は次のようになっています。

```sh
portfolio/
└── docs
    ├── .npmignore
    ├── package.json
    └── src
        ├── 'config' ------------------ 📄 configページ
        │   └── README.md
        ├── 'guide' ------------------- 📄 guideページ
        │   ├── README.md
        │   └── using-vue.md
        ├── 'index.md' ---------------- 🏠 Welcomeページ
        └── '.vuepress' --------------- 📗 メタデータ
            ├── components
            │   ├── demo-component.vue
            │   ├── Foo
            │   │   └── Bar.vue
            │   └── OtherComponent.vue
            ├── 'config.js' ----------- ⚙️ 設定
            ├── enhanceApp.js
            └── styles
                ├── index.styl
                └── palette.styl
```

portfolio の下に **docs** というディレクトリがあります。npm の操作などは docs 配下で行います。
docs のさらに下に **src** というディレクトリがあり、ここでコンテンツの作成を行います。
各ファイル/ディレクトリについては次の通りです。

- **config/ , guide/**
  VuePress が用意したサンプルページです。
  ここを書き換えてポートフォリオを作成していきます。

- **index.md**
  最初に表示されるトップページについて書かれています。

- **.vuepress/**
  VuePress のメタデータを扱うファイルが入っています。
  全体の設定やデザインはこの中のファイルを操作して変更します。

- **.vuepress/config.js**
  VuePress の設定についてはこのファイルに記述します。

::: message
今回は利用しないものについては割愛しています。
:::

# node モジュールをインストールする

まだ必要なモジュールが揃っていないのでインストールしていきます。
doxs ディレクトリに移動して次のコマンド実行してください。

```properties:~/
cd ~/portfolio/docs
npm install
```

# ローカルでプレビューする

VuePress をローカルでプレビューします。
用意されているコマンドがあるのでそれを実行します。

```properties:~/portfolio/docs
npm run dev
```

**success**と出力されたら CloudShell の**ウェブでプレビュー**をクリックします。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/GCP_cloudshell_3.png?version=1)

別のタブが開いて VuePress の Welcome ページが表示されるかと思います。
サンプルとして Guide と Config というページが用意されているのも確認できますね。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/VuePress_preview.gif?version=1)

これで VuePress の導入は完了です。
このサンプルを改造して自分のポートフォリオサイトを作成していきます。
