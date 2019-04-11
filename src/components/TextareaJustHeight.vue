<template>
  <textarea v-on:input="input" placeholder="テキストを入力" v-model="text"></textarea>
</template>

<script>
export default {
  name: 'TextareaJustHeight',

  data () {
    return {
      text: '',
      height: '',
      length: 0
    }
  },
  updated () {
    this.$emit('input', {
      text: this.$el.value,
      height: this.$el.scrollHeight,
      length: this.$el.value.length
    })
  },
  mounted: function() {
    this.text   = this.value.text
    this.height = this.value.height
    this.length = this.value.length
  },
  props: {
    value: {
      type: Object,
      required: true,
    }
  },
  methods: {
    input: function () {
      this.$el.style.height = '';
      this.$el.style.height = this.$el.scrollHeight +'px';
    },
    handleResize: function() {
      this.input();
    }
  },
  mounted: function () {
    window.addEventListener('resize', this.handleResize)
  },
  beforeDestroy: function () {
    window.removeEventListener('resize', this.handleResize)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
textarea {
  padding: 10px;
  width: 100%;
  height: 45px;
  max-height: 200px;
  background: #fff;
  border-radius: 6px;
  color: #505050;
  resize: none;
  font-family: "メイリオ", Meiryo, monospace, "ヒラギノ角ゴ Pro W3","Hiragino Kaku Gothic Pro", YuGothic, sans-serif;
  font-size: 18px;
  line-height: 1.4;
  box-sizing: border-box;
}
</style>