---
title: "STEP6: 埋め込みページの作成"
---

# Sale ページ

[**Zenn の Books**](https://zenn.dev/wataru72v/books) で教材を販売していきますので、それを表示するページを作成します。
以下のようなページを作成します。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/salepage.png?version=1)

## Zenn Books

ポートフォリオから外部のリソースを見せたい場合、埋め込んでしまうのが良いかと思います。
以下のようにページを編集しましょう。

```markdown:~/work/portfolio/docs/src/sale.md
---
autonav:
  enable: true
  order: 24
---

# Sale

## Zenn Books

<iframe
  src="https://zenn.dev/wataru72v/books"
  style="width: 100%; height: 75vh;">
</iframe>

```

`<iframe>`タグを使って Zenn の私の Books が並ぶページを埋め込んでいます。
`width: 100%`で横幅が 100%、`height: 75vh`で縦幅が 75%となるように調整しています。

# SNS ページ

SNS へのリンクをまとめたページとして Youtube, Twitter, Github を埋め込みます。
以下のようなページを作成します。

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/embed.gif?version=1)

## ナビバー設定

ナビバーの設定は同様です。

```markdown:~/work/portfolio/docs/src/sns.md(抜粋)
---
autonav:
  enable: true
  order: 32
---
```

## Youtube

[Youtube のドキュメント](https://support.google.com/youtube/answer/171780?hl=ja)を参考に [Youtube スタートガイド](https://support.google.com/youtube/answer/171780?hl=ja)の再生リストを埋め込みます。
以下の手順を実行してください。

- [Youtube スタートガイド](https://support.google.com/youtube/answer/171780?hl=ja)に移動
- URL の`list=`以下の文字をコピー
  - ここでは`PLpjK416fmKwQKmatriVu3rdwv7g4ZJSfD`をコピー
- **共有 > 埋め込む** の順にクリック
- `src=`以下の URL を`https://www.youtube.com/embed/videoseries?list=コピーした文字`に書き換え
  - ここでは以下のようになる
    `https://www.youtube.com/embed/videoseries?list=PLpjK416fmKwQKmatriVu3rdwv7g4ZJSfD`
- **コピー**をクリック

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/youtube1.png?version=1)

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/youtube2.png?version=1)

- コピーした内容を以下のように貼り付ける

```markdown:~/work/portfolio/docs/src/sns.md(抜粋)
## Youtube

<br />
<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLpjK416fmKwQKmatriVu3rdwv7g4ZJSfD" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

```

これで再生リストの埋め込みは完了です。

## Twitter

[Twitter のドキュメント](https://help.twitter.com/ja/using-twitter/embed-twitter-feed)を参考に [私のタイムライン](https://twitter.com/_wataruv)を埋め込みます。
以下の手順を実行してください。

- [https://publish.twitter.com/](https://publish.twitter.com/)に移動
- 検索窓にユーザー ID を入力
  - ここでは`@_wataruv`を入力
- **Embedded Timeline > set customization options** の順にクリック
- `Height`, `Width`に適当な値を入力
  - 後ほどパーセント表記に書き換えます
- **Update > Copy Code** の順にクリック

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/twitter.png?version=1)

- コピーした内容を以下のように貼り付ける
- `data-width`, `data-height`をパーセント表記に修正
  - `data-width="220" data-height="200"` -> `data-width=75% data-height=60vh`

```diff:~/work/portfolio/docs/src/sns.md(抜粋)
## Twitter

<br />
- <a class="twitter-timeline" data-width="220" data-height="200" href="https://twitter.com/_wataruv?ref_src=twsrc%5Etfw">Tweets by _wataruv</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
+ <a class="twitter-timeline" data-width=75% data-height=60vh href="https://twitter.com/_wataruv?ref_src=twsrc%5Etfw">Tweets by _wataruv</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
```

これでタイムラインの埋め込みは完了です。

## Github

データを表示するのに [GitHub Readme Stats](https://github.com/anuraghazra/github-readme-stats) 、芝を表示するのに [grass-graph](https://grass-graph.moshimo.works/) を利用します。

### GitHub Readme Stats

[GitHub Readme Stats](https://github.com/anuraghazra/github-readme-stats)の次の部分を参考に記述します。

> GitHub Stats Card
>
> ```markdown
> [![Anurag's github stats](https://github-readme-stats.vercel.app/api?username=anuraghazra)](https://github.com/anuraghazra/github-readme-stats)
> ```
>
> Top Languages Card
>
> ```markdown
> [![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=anuraghazra&layout=compact)](https://github.com/anuraghazra/github-readme-stats)
> ```

以下のようにファイルを編集してください。
画像をクリックすることで自分のプロフィール画面へ飛ぶようにしています。

```markdown:~/work/portfolio/docs/src/sns.md(抜粋)
## Github

[![](https://github-readme-stats.vercel.app/api?username=wataru72v)![](https://github-readme-stats.vercel.app/api/top-langs/?username=wataru72v&layout=compact)](https://github.com/wataru72v)
```

### grass-graph

[grass-graph](https://grass-graph.moshimo.works/)から画像の挿入タグを取得します。
以下の手順を実行して下さい。

- [https://grass-graph.moshimo.works](https://grass-graph.moshimo.works)に移動
- 検索窓に自分のユーザー ID を入力する
  - ここでは`wataru72v`を入力
- 出力された`<img>`タグをコピー

![](https://github.com/wataru72v/zenn/raw/main/books/wataru72v-vuepress-portfolio/image/grass.png?version=1)

- コピーした内容を以下のように貼り付ける
- 画像クリックで自分のプロフィールへ飛ぶように`<a>`タグで囲む

```markdown:~/work/portfolio/docs/src/sns.md(抜粋)
<a href="https://github.com/wataru72v" target="_blank" rel="noopener">
  <img src="https://grass-graph.moshimo.works/images/wataru72v.png">
</a>
```

これで Github の埋め込みは完了です。

## SNS ページ全文

SNS ページ全文は以下のようになります。

:::details SNS ページ全文

```markdown:~/work/portfolio/docs/src/sns.md
---
autonav:
  enable: true
  order: 32
---

# SNS

## Youtube

<br />
<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLpjK416fmKwQKmatriVu3rdwv7g4ZJSfD" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Twitter

<br />
<a class="twitter-timeline" data-width=75% data-height=60vh href="https://twitter.com/_wataruv?ref_src=twsrc%5Etfw">Tweets by \_wataruv</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## Github

[![](https://github-readme-stats.vercel.app/api?username=wataru72v)![](https://github-readme-stats.vercel.app/api/top-langs/?username=wataru72v&layout=compact)](https://github.com/wataru72v)

<br />
<a href="https://github.com/wataru72v" target="_blank" rel="noopener">
  <img src="https://grass-graph.moshimo.works/images/wataru72v.png">
</a>
```

:::
