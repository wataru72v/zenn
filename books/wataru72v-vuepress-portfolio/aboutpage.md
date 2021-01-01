---
title: "STEP5: Aboutページの作成"
---

About ページとして次のようなページを作成していきます。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/aboutpage.png?version=1)

# MD ファイルの作成

不要なページの削除と追加するページの作成を行います。
サンプルページはここでは不要なため削除してしまいましょう。
以下ターミナルから実行してください。

```properties:~/work/portfolio/docs/src/
rm -rf config/
rm -rf guide/
```

次に`about.md`, `service.md`, `product.md`, `sns.md`を作成します。
以下ターミナルから実行してください。

```properties:~/work/portfolio/docs/src/
touch about.md
touch product.md
touch sns.md
```

これで次のようなファイル構造になります。

```sh
portfolio/
└── docs
    ├── .npmignore
    ├── package.json
    └── src
        ├── 'about.md' ---------------- 📄 aboutページ
        ├── 'product.md' -------------- 📄 productページ
        ├── 'sns.md' ------------------ 📄 snsページ
        ├── 'index.md' ---------------- 🏠 トップページ
        └── '.vuepress' --------------- 📗 メタデータ
            ├── components
            ├── 'config.js' ----------- ⚙️ 設定
            ├── enhanceApp.js
            └── styles
```

# ナビバー設定

ナビバーに表示させる設定を記述します。

```markdown:~/work/portfolio/docs/src/about.md(抜粋)
---
autonav:
  enable: true
  order: 8
---
```

`order` はナビバーの並び替えで利用する数字で、小さいほど左側に来ます。
後から間への差し込みなどができるように、以降も 8 の倍数の値を設定してきます。

# Profile

プロフィール部分を以下のように記入します。
好みの画像、文字で作成してください。
画像の挿入は markdown 記法でも可能ですが、サイズを小さくするために`<img>`タグを利用しています。

```markdown:~/work/portfolio/docs/src/about.md(抜粋)
# About

## Profile

<img src="wataru_icon.png" width=33%>

**名前： ワタル**

2021 年から活動を開始。
世の中の役に立つサービスを作ることを目標に個人開発を行う。
好きなことはプログラミングと毛布にくるまって眠ること。
大好物はサツマイモ。
```

# Skills

スキル部分は画像を並べて表現しています。
アイコンを挿入した時と同様の手順で画像を`.vuepress/public`にアップロードします。
以下の手順を実行してください。

- `public/`上で右クリック
- **Upload Files** をクリック
- 好みの画像をアップロード

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/modimage.png?version=1)

ここでは`html.png`, `css.png`, `js.png`, `nodejs.png`, `vuejs.png` の 5 つをアップしました。

次に以下のように記入します。

```markdown:~/work/portfolio/docs/src/about.md(抜粋)
## Skills

<template>
  <img class="skill" v-for="image in images" :src="image.path"/>
</template>

<style>
.skill {
  width: 19%;
  margin: 3%;
}
</style>

<script>
export default {
  data() {
    return {
      images: [
        { path: "html.png" },
        { path: "css.png" },
        { path: "js.png" },
        { path: "nodejs.png" },
        { path: "vuejs.png" },
      ],
    };
  },
};
</script>
```

VuePress では markdown ファイルの中で vue.js が利用できます。
ここでは images の配列の中の要素を for 文で回すようにして画像を表示させています。
画像サイズは margin 込みで 25%になるように調整しています。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/skill.png?version=1)

# About ページ全文

About ページの全文は以下のようになります。

:::details About ページ全文

```markdown:~/work/portfolio/docs/src/about.md
---
autonav:
  enable: true
  order: 8
---

# About

## Profile

<img src="wataru_icon.png" width=33%>

**名前： ワタル**

2021 年から活動を開始。
世の中の役に立つサービスを作ることを目標に個人開発を行う。
好きなことはプログラミングと毛布にくるまって眠ること。
大好物はサツマイモ。

## Skills

<template>
  <img class="skill" v-for="image in images" :src="image.path"/>
</template>

<style>
.skill {
  width: 19%;
  margin: 3%;
}
</style>

<script>
export default {
  data() {
    return {
      images: [
        { path: "html.png" },
        { path: "css.png" },
        { path: "js.png" },
        { path: "nodejs.png" },
        { path: "vuejs.png" },
      ],
    };
  },
};
</script>
```

:::
