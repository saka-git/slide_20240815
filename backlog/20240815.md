---
theme: seriph
background: https://richka.co/wp-content/uploads/2020/09/anders-jilden-uwbajDCODj4-unsplash.jpg
---

<!-- 背景画像とテキストアニメーション -->

<div
  v-motion
  :initial="{ opacity: 0, y: 50 }"
  :enter="{ opacity: 1, y: 0, transition: { delay: 500 } }"
  class="text-center text-5xl font-bold"
>
  Slidev使う
</div>

<style>
section {
  background-image: url('https://richka.co/wp-content/uploads/2020/09/anders-jilden-uwbajDCODj4-unsplash.jpg');
  background-size: cover;
  color: #ffffff;
}
</style>

---

# おすすめポイント

- git管理できる
- マークダウンで書ける
- プレゼンターモードできる
- コードブロックでハイライトできる
- カスタムコンポーネントができる
- htmlで書ける
- vscode拡張機能あり
- 簡単にデプロイできる！

---

# 使い方

## インストール

```bash
npm init slidev
```

## アクセス

http://localhost:3030/1

<div class="p-5 bg-teal-600 text-white rounded-lg shadow-md mt-10">
  スライドの使い方は簡単です！
</div>
---

# 使い方その2

- slides.mdに記述
- 別ファイルをインポートしてもOK（ページごとにファイル分けれる）
  <img src="/screenshot1.png" class=" h-90 rounded shadow" />

---

# 使い方その3

`---`でページ間を区切り、あとはマークダウン
<img src="/screenshot2.png" class=" h-90 rounded shadow" />

---

# コードについて

コードブロックを直接使用してハイライト表示する

```ts {2,3}
function add(a: Ref<number> | number, b: Ref<number> | number) {
  return computed(() => unref(a) + unref(b));
}
```

````
```ts {2,3}
function add(a: Ref<number> | number, b: Ref<number> | number) {
  return computed(() => unref(a) + unref(b));
}
````

編集したい場合は、monacoを使う

```ts {monaco}
console.log("HelloWorld");
```

<div v-click>
  <div class="text-lg text-red-600 mt-5">
    実際のコードをハイライトして表示できます！
  </div>
</div>

---

# 装飾

Windi CSSとVueコンポーネントを直接使用して、スライドをスタイリングし、リッチにすることができます。

<div class="p-3">
  <Tweet id="20" />
</div>

```
<div class="p-3">
  <Tweet id="20" />
</div>
```

---

# 装飾2

> Hello `world`

```
<style>
blockquote {
  code {
    @apply text-teal-500 dark:text-teal-400;
  }
}
</style>
```

<style>
blockquote {
  code {
    @apply text-teal-500 dark:text-teal-400;
  }
}
</style>

---

# 画像

リモート

`![リモートの画像](https://sli.dev/favicon.png)`
![リモートの画像](https://sli.dev/favicon.png)

---

# 画像

ローカル

`![ローカルの画像](/zod.svg)`
![ローカルの画像](/zod.svg)

---

# 図形

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

```
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

---

# アニメーション

<!-- コンポーネントの使い方: "次へ"を押すまで、ここから下の内容は表示されません -->
<v-click>

Hello World

</v-click>

<!-- ディレクティブの使い方: 2回目の"次へ"を押すまで、ここから下の内容は表示されません -->
<div v-click class="text-xl p-2">

Hey!

</div>
```
<!-- コンポーネントの使い方: "次へ"を押すまで、ここから下の内容は表示されません -->
<v-click>
Hello World
</v-click>
<!-- ディレクティブの使い方: 2回目の"次へ"を押すまで、ここから下の内容は表示されません -->
<div v-click class="text-xl p-2">
Hey!
</div>
```

---

# アニメーション2

<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }">
  Slidev
</div>

```
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }">
  Slidev
</div>
```

---

#プレゼンターモード

http://localhost:3030/presenter

---

# デプロイ方法

- Netlify
- Vercel
- Github Pages

---

# Vercel

0. 設定（vercel.jsonに記述、インストール時に同時作成済み）
1. プロジェクト作成
2. リポジトリ連携
3. 完了

---

<div style="
position:absolute;
left:50%;
top:50%;
z-index:100;
font-size:100px
">

Fin.

</div>
