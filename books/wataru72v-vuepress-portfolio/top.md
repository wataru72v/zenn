---
title: "STEP4: トップページの編集"
---

トップページを編集していきます。
次のようなトップページを作成します。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/modtop.png?version=1)

# タイトルの変更

タイトルを変更するときは設定ファイルから編集します。
これでトップページ中央の文字と左上のトップへのリックの文字が変更されます。

```diff:~/work/portfolio/docs/src/.vuepress/config.js(抜粋)
module.exports = {
- title: "Vuepress Docs Boilerplate",
+ title: "Wataru Docs",
  description: description,
...
}
```

# アクセントカラーの変更

デフォルトのアクセントカラーは Vue などで使われてる緑色ですが、変更することも可能です。
アクセントカラーを変更するには`.vuepress/styles/palette.styl`を次のように編集します。

```diff:~/work/portfolio/docs/src/.vuepress/styles/palette.styl
- $accentColor = #3eaf7c
+ $accentColor = #673AB7
$textColor = #2c3e50
$borderColor = #eaecef
$codeBgColor = #282c34
```

今回はアイコンのキャラクターと揃えて紫色にしました。
これでボタンなどの色が変更されます。

# 画像の変更

VuePress では画像は`.vuepress/`配下の`public/`に配置するという決まりがあります。
以下コマンドを実行して`public/`フォルダを作成します。

```properties:~/work/portfolio/docs/src
mkdir .vuepress/public
```

`public/`の中に画像をアップロードします。
以下の手順を実行してください。

- `public/`上で右クリック
- **Upload Files** をクリック
- 好みの画像をアップロード

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/modimage.png?version=1)

ここではワタル君の画像に`wataru_icon.png`と名前をつけてアップロードしました。

画像を利用する際は`.vuepress/public/`からの相対パスで指定します。
以下のようにファイルを編集します。

```diff:~/work/portfolio/docs/src/index.md(抜粋)
---
home: true
- heroImage: https://v1.vuepress.vuejs.org/hero.png
+ heroImage: wataru_icon.png
---
```

# ナビバーへの非表示

トップページはナビバー表示させないようにしたいため、
以下のように **autonav** の値を disable にしておきます。

```diff:~/work/portfolio/docs/src/index.md(抜粋)
---
home: true
+ autonav:
+   enable: false
heroImage: wataru_icon.png
---
```

# 内容の変更

他内容を変更します。
好みの文章を記述してください。

```diff:~/work/portfolio/docs/src/index.md
---
home: true
autonav:
  enable: false
heroImage: wataru_icon.png
- tagline: portfolio site
- actionText: Quick Start →
- actionLink: /guide/
- - title: Feature 1 Title
-   details: Feature 1 Description
- - title: Feature 2 Title
-   details: Feature 2 Description
- - title: Feature 3 Title
-   details: Feature 3 Description
- footer: Made by wataru with ❤️
+ tagline: null
+ actionText: About me →
+ actionLink: /about.md
+ features:
+   - title: サービス開発
+     details: 自分の作品を世に発表したいという思いから、WEBサービスの開発を行っています。サービスを開発しながら、技術のキャッチアップ、情報のアウトプットなども行っていきます。
+   - title: 動画投稿
+     details: 開発の様子や有益な情報を動画やライブ配信を通して共有します。自分のモチベーションを上げ、同時に視聴者のモチベーションを上げられるようなコンテンツを目指します。
+   - title: 学習教材
+     details: 活動の中で得られた知見や情報は学習教材に落とし込み販売します。ここで得た資金はサービスの開発/運用費、動画や次の学習教材の質を向上させるために活用します。
+ footer: © 2021 wataru
---
```

# トップページ全文

最終的なトップページは以下のようになります。
これで冒頭の画像のようなトップページの完成です。

```markdown:~/work/portfolio/docs/src/index.md
---
home: true
autonav:
  enable: false
heroImage: wataru_icon.png
actionText: About me →
actionLink: /about.md
features:
  - title: サービス開発
    details: 自分の作品を世に発表したいという思いから、WEBサービスの開発を行っています。サービスを開発しながら、技術のキャッチアップ、情報のアウトプットなども行っていきます。
  - title: 動画投稿
    details: 開発の様子や有益な情報を動画やライブ配信を通して共有します。自分のモチベーションを上げ、同時に視聴者のモチベーションを上げられるようなコンテンツを目指します。
  - title: 学習教材
    details: 活動の中で得られた知見や情報は学習教材に落とし込み販売します。ここで得た資金はサービスの開発/運用費、動画や次の学習教材の質を向上させるために活用します。
footer: © 2021 wataru
---
```
