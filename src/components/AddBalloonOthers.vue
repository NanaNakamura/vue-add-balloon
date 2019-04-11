<template>
  <div class="balloon">
    <figure>
      <img v-bind:src="icon">
      <figcaption>{{ name }}</figcaption>
    </figure>
    <p>{{ text }}</p>
  </div>
</template>

<script>
export default {
  name: 'AddBalloonOthers',
  data () {
    return {
    }
  },
  props: ['name', 'text', 'icon']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
$imageWidth: 60px;
$background: #eeeeee;

.balloon {
  position: relative;
  padding-left: $imageWidth + 14px;
  min-height: $imageWidth;
  figure {
    img {
      position: absolute;
      left: 0;
      top: 0;
      border-radius: 50%;
      width: $imageWidth;
    }
    figcaption {
      max-width: 80%;
      color: gray;
      font-family: 'Montserrat', sans-serif;
      font-size: 1.2rem;
      letter-spacing: 0.04em;
      word-break: break-all;
    }
  }
  p {
    position: relative;
    display: inline-block;
    max-width: 80%;
    margin-top: 6px;
    padding: 12px 16px;
    border-radius: 20px;
    border-top-left-radius: 0px;
    background: $background;
    font-size: 1.6rem;
    line-height: 1.4;
    word-break: break-all;
    &::before {
      content: '';
      position: absolute;
      left: -6px;
      top: 0;
      border: 10px solid transparent;
      border-top: 16px solid $background;
      border-right: 10px solid $background;
      pointer-events: none;
    }
  }
}
</style>
