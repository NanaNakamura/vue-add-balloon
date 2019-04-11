<template>
  <div id="app">
    <h1>Add Balloon at chat</h1>
    <div class="frame">
      <div class="header">Balloon sample</div>
      <div class="main" ref="main">
        <AddBalloonOthers
          name="hotkun"
          text="今日は元気ですか？"
          icon="static/assets/images/icon1.png"
        />
      </div>
      <div class="input-area">
        <form v-on:submit.prevent="add">
          <TextareaJustHeight ref="texts" v-model="data"/>
          <button><i class="material-icons">Send</i></button>
        </form>
      </div>
    </div>

    <h2>Add others balloon (left)</h2>
    <form class="sub" v-on:submit.prevent="addOthers">
      <dl>
        <dt>name<span>＊</span></dt>
        <dd><input type="text" v-model="sub.name"></dd>
        <dt>text<span>＊</span></dt>
        <dd><input type="text" v-model="sub.text"></dd>
        <dt>icon url</dt>
        <dd><input type="icon" v-model="sub.icon" placeholder="http://placehold.it/200x200"></dd>
      </dl>
      <button><i class="material-icons">Send</i></button>
    </form>
  </div>
</template>

<script>
import TextareaJustHeight from './components/TextareaJustHeight'
import AddBalloonSelf from './components/AddBalloonSelf'
import AddBalloonOthers from './components/AddBalloonOthers'
import Vue from 'vue'

export default {
  name: 'App',
  components: {
    TextareaJustHeight,
    AddBalloonSelf,
    AddBalloonOthers
  },
  data () {
    return {
      data: {
        text: '',
        height: ''
      },
      sub: {
        name: '',
        text: '',
        icon: ''
      },
      balloonTexts: []
    }
  },
  methods: {
    // self balloon 追加用
    add: function () {
      if(this.$refs.texts.$el.value === '') {
        return;
      }

      // コンポーネントを追加
      let balloon = Vue.extend(AddBalloonSelf)
      let instance = new balloon({
        propsData: {
          text: this.$refs.texts.$el.value
        }
      }).$mount()
      this.$refs['main'].appendChild(instance.$el)

      // データを追加
      this.balloonTexts.push({
        category: 'self',
        text: this.$refs.texts.$el.value
      })

      // 入力エリアをreset
      this.$refs.texts.$el.value = '';
      this.$refs.texts.input();
    },
    // others balloon 追加用
    addOthers: function () {
      if(this.sub.name === '' || this.sub.text === '') {
        return;
      }

      // iconが空だった場合 デフォルトのにする
      if(this.sub.icon === ''){
        this.sub.icon = 'static/assets/images/icon2.png'
      }

      // コンポーネントを追加
      let balloon = Vue.extend(AddBalloonOthers)
      let instance = new balloon({
        propsData: {
          name: this.sub.name,
          text: this.sub.text,
          icon: this.sub.icon
        }
      }).$mount()
      this.$refs['main'].appendChild(instance.$el)

      // データを追加
      this.balloonTexts.push({
        category: 'other',
        name: this.sub.name,
        text: this.sub.text,
        icon: this.sub.icon
      })

      // 入力エリアをreset
      this.sub.name = '';
      this.sub.text = '';
      this.sub.icon = '';
    }
  }
}
</script>

<style lang="scss" module>
@import "../node_modules/formula-css/develop/formula.scss";
</style>
<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin: 100px 4%;
  h1 {
    margin-bottom: 20px;
    font-size: 2em;
    font-weight: bold;
    text-align: center;
  }
  h2 {
    margin-top: 80px;
    margin-bottom: 20px;
    font-size: 1.5em;
    font-weight: bold;
    text-align: center;
  }
  .frame {
    max-width: 480px;
    height: 600px;
    margin: 0 auto;
    overflow: hidden;
    border-radius: 10px;
    box-shadow: 2px 6px 20px rgba(#000, 0.2);
    display: flex;
    flex-direction: column;
    justify-content:flex-end;
    .header {
      background: #20c4cb;
      color: #fff;
      font-family: 'Montserrat', sans-serif;
      font-size: 1.8rem;
      font-weight: bold;
      line-height: 60px;
      letter-spacing: 0.04em;
      text-align: center;
    }
    .main {
      width: 100%;
      padding: 20px 10px;
      overflow-y: auto;
      .balloon + .balloon {
        margin-top: 20px;
      }
    }
    .input-area {
      margin-top: auto;
      padding: 10px;
      background: rgba(#20c4cb, 0.1);
      form {
        display: flex;
        align-items: flex-end;
        button {
          width: 100px;
          height: 45px;
          border-radius: 6px;
          margin-left: 10px;
          background: #20c4cb;
          color: #fff;
          font-family: 'Montserrat', sans-serif;
          font-weight: bold;
          line-height: 45px;
          text-align: center;
          i {
            display: block;
            font-size: 1.4rem;
            font-style: normal;
            letter-spacing: 0.04em;
          }
        // .material-icons {
        //   font-family: 'Material Icons';
        //   font-weight: normal;
        //   font-style: normal;
        //   font-size: 24px;  /* Preferred icon size */
        //   display: inline-block;
        //   line-height: 1;
        //   text-transform: none;
        //   letter-spacing: normal;
        //   word-wrap: normal;
        //   white-space: nowrap;
        //   direction: ltr;

        //   -webkit-font-smoothing: antialiased;
        //   text-rendering: optimizeLegibility;

        //   -moz-osx-font-smoothing: grayscale;
        //   font-feature-settings: 'liga';
        // }
        }
      }
    }
  }
  .sub {
    width: 480px;
    margin: 0 auto;
    dl {
      dt {
        margin-top: 20px;
        margin-bottom: 10px;
        span {
          color: red;
        }
      }
    }
    input {
      width: 100%;
      border-radius: 6px;
      background: #eeeeee;
      padding: 10px 14px;
      font-size: 1em;
    }
    button {
      display: block;
      width: 200px;
      height: 45px;
      border-radius: 6px;
      margin: 20px 0 0 auto;
      background: #20c4cb;
      color: #fff;
      font-family: 'Montserrat', sans-serif;
      font-weight: bold;
      line-height: 45px;
      text-align: center;
      i {
        display: block;
        font-size: 1.4rem;
        font-style: normal;
        letter-spacing: 0.04em;
      }
    // .material-icons {
    //   font-family: 'Material Icons';
    //   font-weight: normal;
    //   font-style: normal;
    //   font-size: 24px;  /* Preferred icon size */
    //   display: inline-block;
    //   line-height: 1;
    //   text-transform: none;
    //   letter-spacing: normal;
    //   word-wrap: normal;
    //   white-space: nowrap;
    //   direction: ltr;

    //   -webkit-font-smoothing: antialiased;
    //   text-rendering: optimizeLegibility;

    //   -moz-osx-font-smoothing: grayscale;
    //   font-feature-settings: 'liga';
    // }
    }
  }
}
</style>
