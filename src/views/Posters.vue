<template>
  <div class="component-poster" v-show="visible">
    <div class="mask" @click='close'>
      <header class="poster-header"></header>
      <div class="poster-list">
        <div class="poster" v-for="(item, index) in posters" v-bind:key="index">
          <img :src="item.url" alt="">
          <div class="title">{{item.title}}</div>
        </div>
      </div>
      <footer class="poster-footer"></footer>
    </div>
  </div>
</template>
<script>
import poster from '../img/poster.jpg'
export default {
  name: 'Posters',
  data () {
    return {
      visible: false,
      posters: [
        {
          title: '2019.07.01期',
          url: poster
        },
        {
          title: '2019.07.01期',
          url: poster
        },
        {
          title: '2019.07.01期',
          url: poster
        },
        {
          title: '2019.07.01期',
          url: poster
        }
      ]
    }
  },
  methods: {
    open () {
      this.visible = true
    },
    close () {
      this.visible = false
      // this.$nextTick(() => {
      //   this.$emit('closed')
      // })
    }
  }
}
</script>
<style>
  .mask{
    position: fixed;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    z-index: 10;
    overflow: auto;
    background-color: rgba(0,0,0,.86);
  }
  .poster-header{
    width: 28.89rem;
    height : 2rem;
    margin: 3rem auto 0;
    background: url(../img/poster-header.png) no-repeat;
    background-size: 100% auto;
  }
  .poster-list{
    width: 28.89rem;
    min-height: 10rem;
    margin: 0 auto;
    background: url(../img/poster-bg.png) repeat-y;
    background-size: 100% auto;
  }
  .poster{
    width: 13.38rem;
    height: 22.85rem;
    display: inline-block;
    margin: .5rem .5rem 0;
    padding-top: 1.38rem;
    background: url(../img/poster-border.png) no-repeat;
    background-size: 100% auto;
    font-size: 1rem;
  }
  .poster img{
    width: 12rem;
    display: block;
    margin: 0 auto;
  }
  .poster div{
    position: relative;
    top: .3rem;
    text-align: center;
  }
  .poster-footer{
    width: 28.89rem;
    height : 1.76rem;
    margin: 0 auto 3rem;
    background: url(../img/poster-footer.png) no-repeat;
    background-size: 100% auto;
  }
</style>
