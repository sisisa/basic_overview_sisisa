## Vue.js

- [Vue.jsとは?](#Vue.jsとは?)
- [Vue.jsの特徴](#Vue.jsの特徴)
- [Vueの基本機能](#Vueの基本機能)

- Vue.js公式ページ
https://ja.vuejs.org/guide/introduction.html
# 基本事項

## Vue.jsとは?
- Vue.jsは、Webサイトやアプリの見た目（画面）をつくるための道具です
- JavaScriptを使って、ボタンを押すと画面が変わるなどの仕組みをかんたんにつくることができる

- Vueは、はじめはシンプルに使えて、あとからだんだん高度なこともできるようになる「成長できる道具（プログレッシブ・フレームワーク）」

## Vue.jsの特徴
- HTML・CSS・JavaScriptの上に作られている
→ ふつうのWeb開発と組み合わせやすい

- コンポーネントベースの設計
→ 画面のパーツを部品のように分けて作ることができる

- 宣言的なスタイル
→ 「こうなってほしい」という形でコードを書くことができる

## Vueの基本機能
1. 宣言的レンダリング

Vueでは、HTMLの中に変数をそのまま使えます。
```html
<p>{{ message }}</p>
```
JavaScriptで message = "こんにちは" とすれば、画面にはそのまま「こんにちは」と表示されます。

2. リアクティビティ
JavaScriptのデータが変わると、Vueは自動で画面を更新してくれます。
開発者が画面の表示をいちいち書き換える必要がありません。


## プログレッシブフレームワーク
- プログレッシブとは進歩的(良い方に進み変わっていくこと)という意味
- Vueは、「必要に応じて機能を追加していける仕組み」を持っています。
- 小さく作り始めて、大きなアプリにも育てられます。

### 使い方の例
| 使い方                            | 内容                                          |
| --------------------------------- | --------------------------------------------- |
| HTMLに直接組み込む                | 小さなスクリプトを追加するだけでVueを使える   |
| Webページの一部として使う         | 特定のエリアだけVueでつくる                   |
| シングルページアプリ（SPA）       | ページを切り替えずに動くアプリをVueだけで作る |
| サーバーサイドレンダリング（SSR） | サーバーと連携しながら表示を高速にする        |
| 静的サイトジェネレーション（SSG） | 事前にページを作っておき、高速に読み込ませる  |
| モバイル・デスクトップアプリなど  | スマホやPC用のアプリ開発にもVueが使える       |

## 単一ファイルコンポーネント(SFC)
- Vueでは、1つのファイルに「見た目」「動き」「デザイン」をまとめて書くことができます。
- この形式をSFC**（Single File Component）**と呼びます。

```vue
<template>
  <h1>{{ title }}</h1>
</template>

<script>
export default {
  data() {
    return {
      title: 'こんにちは Vue!'
    }
  }
}
</script>

<style>
h1 {
  color: green;
}
</style>
```
このように、1つのvueファイルで全部まとめて管理できるため、整理しやすくなります。


## Composition API
- Vue3では、Composition APIという新しい書き方が使えます。
- 複雑なロジックをまとめやすく、読みやすいコードになります。

```vue
<template>
  <p>{{ count }}</p>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>
```

<script setup> を使うと、テンプレートの中で変数や関数をそのまま使うことができます。
