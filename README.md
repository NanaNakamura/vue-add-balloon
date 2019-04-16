# vue-add-balloon

LINEとかのチャット風な吹き出しがセットになったコンポーネント。  
吹き出しがメインなコンポーネントです。  


💬<a href="https://nananakamura.github.io/c/vue-add-balloon/index.html" target="_blank">Demo</a>


## Usage

### HTML
#### チャット風フレーム（吹き出しセット） ※おまけ
```
<template>
  <ChatFrame />
</template>
```

#### 自分の吹き出し
```
<template>
  <AddBalloonSelf
    text="テキスト"
  />
</template>
```
`text` は必須

#### 相手の吹き出し
```
<template>
  <AddBalloonOthers
    name="なまえ"
    text="テキスト"
    icon="アイコンの画像パス"
  />
</template>
```
`name` `text` は必須  
`icon` は空でも可


### scripts

.vueファイルコンポーネントフォルダーにコピペして、  
componentsに追加？

#### ChatFrameの場合
```
import ChatFrame from './components/ChatFrame'

export default {
  components: {
    ChatFrame
  }
}
```

#### ChatFrame.vue について

template内に色々書いているけど、  
実際あれば良い部分はdiv.frameなので、  
他の部分は、プレビュー用においているソースなので削除してください

[TextareaJustHeight.vue](https://github.com/NanaNakamura/vue-textarea-justheight) をついでに使っています。

吹き出しの内容は `balloonTexts` に格納されます  
`"category": "self"` の場合は自分の吹き出し  
`"category": "other"` の場合は相手の吹き出し


## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# SCSSを有効化
npm install sass-loader node-sass --save-dev

<style lang="scss">
/* write SASS! */
</style>

# reset CSSをインストール
npm install --save formula-css
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
