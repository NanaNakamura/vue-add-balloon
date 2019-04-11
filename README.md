# vue-add-balloon

LINEとかのチャット風な吹き出しがセットになったコンポーネント。  
吹き出しがメインなコンポーネントです。  


💬<a href="https://nananakamura.github.io/c/vue-add-balloon/index.html" target="_blank">Demo</a>


## Usage

### HTML
#### 自分の吹き出し
```
<template>
  <AddBalloonSelf
    text="テキスト"
  />
</template>
```

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


### scripts

.vueファイルコンポーネントフォルダーにコピペして、  
componentsに追加？

```
import AddBalloonSelf from './components/AddBalloonSelf'
import AddBalloonOthers from './components/AddBalloonOthers'

export default {
  components: {
    AddBalloonSelf,
    AddBalloonOthers
  }
}
```


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
