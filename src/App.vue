<template>
  <div id="app">
    <h1>Add Balloon at chat</h1>
    <ChatFrame />
  </div>
</template>

<script>
import ChatFrame from './components/ChatFrame'

export default {
  name: 'App',
  components: {
    ChatFrame
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
  pre {
    margin-bottom: 20px;
    padding: 40px;
    border-radius: 6px;
    background: #f5f5f5;
  }
  p {
    line-height: 1.6;
  }
}
</style>