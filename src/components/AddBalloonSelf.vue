<template>
  <div class="balloon">
    <p>{{ text }}</p>
  </div>
</template>

<script>
export default {
  name: 'AddBalloonSelf',
  data () {
    return {
    }
  },
  props: ['text']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
$background: #20c4cb;

.balloon {
  text-align: right;
  p {
    position: relative;
    display: inline-block;
    max-width: 80%;
    margin-right: 6px;
    padding: 12px 16px;
    border-radius: 20px;
    border-top-right-radius: 0px;
    background: $background;
    color: #fff;
    font-size: 1.6rem;
    line-height: 1.4;
    text-align: left;
    word-break: break-all;
    &::before {
      content: '';
      position: absolute;
      right: -6px;
      top: 0;
      border: 10px solid transparent;
      border-top: 10px solid $background;
      border-left: 10px solid $background;
    }
  }
}
</style>
