<template>
  <div id="app">
    <img width="100%" src="./img/banner.jpg" />
    <act-main />
    <act-draw />
    <act-rewards />
    <Posters ref="posters" v-bind:posters="posters"/>
    <div class="widget" @click="openPosters">
      <img src="./img/widget.png" alt="">
    </div>
    <Rule ref="rule"/>
    <div class="rules" @click="openRule">活动规则</div>
    <div class="foot">
      <img src="./img/foot-btn_03.png" />
      <img src="./img/foot-btn_05.png" />
      <img src="./img/foot-btn_07.png" />
      <img src="./img/foot-btn_09.png" />
      <img src="./img/foot-btn_11.png" />
      <img src="./img/foot-btn_18.png" />
      <img src="./img/foot-btn_19.png" />
      <img src="./img/foot-btn_20.png" />
      <img src="./img/foot-btn_21.png" />
      <img src="./img/foot-btn_22.png" />
    </div>
    <act-follow ref="follow" />
  </div>
</template>

<script>
  import './assets/less/common.less'
  import ActMain from './views/act-main'
  import ActDraw from './views/act-draw'
  import ActRewards from './views/act-rewards'
  import Posters from './views/Posters'
  import Rule from './views/Rule'
  import ActFollow from './views/act-follow'

  // 封面占位图，有真实数据后可删除
  import poster from './img/poster.jpg'

  export default {
    name: 'App',
    components: {
      ActMain,
      ActDraw,
      ActRewards,
      Posters,
      Rule,
      ActFollow
    },
    data () {
      return {
        loading: false,
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
    methods:{
      openRule () {
        this.$refs.rule.open()
      },
      openPosters () {
        this.$refs.posters.open()
      },
      openFollow () {
        this.$refs.follow.open()
      }
    }
  }
</script>

<style>
  #app {
    background: rgb(25, 24, 29) url(./img/background.jpg) repeat;
    background-size: 100%;
    color: rgb(255, 204, 102);
  }
  .widget{
    width: 7.87rem;
    height: 7.34rem;
    position: fixed;
    right: 1.55rem;
    bottom: 19rem;
    line-height: 0;
  }
  .widget img{
    width: 100%;
    height: 100%;
  }
</style>
