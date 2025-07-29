# Defining Store

## 基本概要
- ストアは、Webアプリの「みんなで使うデータ」をまとめておく場所
- Vue.js でデータをたくさんの部品（コンポーネント）と共有したいときに使う
- **Pinia（ピニア）**は、Vueのための「ストアをつくる道具」
- defineStore() という関数を使って、ストアを作る事ができる

## defineStore() の使い方
- ストアには一つの名前 が必要(例:defineStore('counter', {...}))

**Options APIスタイルでの書き方:**
```JS
defineStore('store名', {
  state: () => ({ ... }),       // データ
  getters: { ... },             // 計算したデータ
  actions: { ... }              // 実行する動き
})
```

**Setup関数スタイルでの書き方:**
```JS
defineStore('store名', () => {
  const count = ref(0)          // データ
  function increment() {        // 動き
    count.value++
  }

  return { count, increment }   // 外から使えるようにする
})
```
- Vue の Composition API に近いスタイルで、ref() や computed() を自由に使える

### OptionsとSetupの違い
| 比較項目    | Options               | Setup              |
| ------- | ------------------------- | --------------------- |
| 書き方     | state/getters/actionsで分ける | Composition APIのように書く |
| 柔軟性     | 少なめ                       | 高い（watch, injectも使える） |
| SSR対応   | やりやすい                     | 注意が必要（工夫がいる）          |
| 状態の管理方法 | オブジェクトをreturnする           | すべてのプロパティをreturnする    |

## 注意点・備考
- Setupストアでは、データや関数は全部returnで外に出す必要がある：
- 出さないとPiniaがそれを「使えるデータ」として見つけられません。

- ストアの中でwatchやinjectなども自由に使える
例:watch(count, () => { ... })
例:const route = useRoute()（ただし return してはいけない）
