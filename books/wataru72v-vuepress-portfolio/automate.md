---
title: "STEP3: メニューバーの自動化"
---

ナビバーとサイドバーを一つ一つ記述するのは面倒なので、自動で表示できるようにしていきます。

# ナビバー

ナビバーの表示を自動化させるために[VuePress Plugin Auto Nav Links](https://github.com/webmasterish/vuepress-plugin-autonav)を利用します。

モジュールをインストールします。

```properties:~/portfolio/docs/
npm install -D vuepress-plugin-autonav
```

設定ファイルを以下のように編集します。

```diff:~/portfolio/docs/src/.vuepress/config.js(抜粋)
+ const autonav = {
+   enable: true,
+ };
module.exports = {
  themeConfig: {
-   nav: [
-     {
-       text: "Guide",
-       link: "/guide/",
-     },
-     {
-       text: "Config",
-       link: "/config/",
-     },
-     {
-       text: "VuePress",
-       link: "https://v1.vuepress.vuejs.org",
-     },
-   ],
- },
  plugins: [
    "@vuepress/plugin-back-to-top",
    "@vuepress/plugin-medium-zoom",
+   "autonav",
  ],
};
```

ナビバーで表示したいファイルで次のように記述します。

```markdown
---
title: Page Title

autonav:
  enable: true
  order: -1
---
```

これでナビバーが自動で表示されるようになりました。

# サイドバー

設定ファイルを以下のように編集します。

```diff:~/portfolio/docs/src/.vuepress/config.js(抜粋)
  themeConfig: {
+   sidebar: "auto",
-   sidebar: {
-     "/guide/": [
-       {
-         title: "Guide",
-         collapsable: false,
-         children: ["", "using-vue"],
-       },
-     ],
-   },
  },
```

これで各ファイルの見出しがサイドバーに自動で表示されます。

詳しい設定については[ドキュメントの Sidebar](https://vuepress.vuejs.org/theme/default-theme-config.html#sidebar)を確認してください。

# 設定ファイル全文

設定ファイル全文は次のようになります。

```js:~/portfolio/docs/src/.vuepress/config.js
const { description } = require("../../package");
const autonav = {
  enable: true,
};

module.exports = {
  title: "Vuepress Docs Boilerplate",
  description: description,

  head: [
    ["meta", { name: "theme-color", content: "#3eaf7c" }],
    ["meta", { name: "apple-mobile-web-app-capable", content: "yes" }],
    [
      "meta",
      { name: "apple-mobile-web-app-status-bar-style", content: "black" },
    ],
  ],

  themeConfig: {
    repo: "",
    editLinks: false,
    docsDir: "",
    editLinkText: "",
    lastUpdated: false,
    sidebar: "auto",
  },

  plugins: [
    "@vuepress/plugin-back-to-top",
    "@vuepress/plugin-medium-zoom",
    "autonav",
  ],
};
```
