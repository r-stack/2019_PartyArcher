# ちょきんでGO（仮）


## 開発
- 基本的には srcの下のroutes,layouts/main.vueでルート設定を作る
- Pagesの下に各画面を作成して、ルート設定をすれば動く

## 構成
- src
  - About.vue 使ってない
  - Gacha.vue ガッチャ画面
  - Home.vue ホーム画面（TOP)
  - Present.vue 貯蓄がたまったらほしいものが郵送される画面	
  - Setting.vue いろいろな設定用の画面（一つの画面を使いまわす）

## Build Setup
- node.js

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```



For a detailed explanation of the build process, read the [docs for vue-loader](http://vuejs.github.io/vue-loader).
