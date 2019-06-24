<template>
  <div class="draw">
    <img class="draw__head" src="../img/draw-title.png" />
    <div class="draw__content">
      <div class="draw__content__title">
        <div class="draw__content__title__text">
          <span>我的抽奖次数：{{draw}}次</span>
          <img @click="draw = 999" src="../img/refresh.png" />
        </div>
      </div>
      <div class="draw__content__body"></div>
      <div class="draw__content__end">
        <img @click="draw--" src="../img/draw-btn.png" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      draw: 999
    }
  }
}
</script>
