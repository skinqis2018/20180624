<template>
  <div class="component-rule" v-show="visible">
    <div class="mask" @click='close'>
      <header class="rule-header"></header>
      <div class="rule-warp">
        <ul class="rule-list">
          <li>1活动时间:每周</li>
          <li>2.主播分区:根据每周一零点时，主播近30天开播最多品类自动划分，分区不可调整。</li>
          <li>3.提名主播评选:</li>
          <li>1)“十大人物”候选人评选:给主播赠送大神奖章和鹅蛋，帮主播获得积分，每周十大专区的TOP3成为下周*十大人物”候选人，1个大神奖章= 1积分，用户完成对应"奖章任务”可免费领取大神奖章，每位用户每天的前100个鹅蛋也可为主播增加积分;</li>
          <li>2)“十佳视频”评选:每周用户在页面上对上周30位候选人视频点赞，赞数的TOP10视频为本周“十佳视频",对应主播为当周"十大人物"，用户完成对应点赞任务”可免费获得点赞资格;</li>
          <li>3)“封面人物": TOP1为当周封面人物;</li>
          <li>4.主播奖励:人气奖励:以活动期间主播日均人(值为计算基准，保底5w加成，最高加成不超过30w;个人页奖章将配合app新版本上线时发放;其他牌面奖励将于活动结束后的7个工作日内人工联系发放。</li>
          <li>5.用户奖励:抽奖获得的礼物将即时发放至用户背包。</li>
          <li>6.腾讯公司保留法律范围内对活动规则进行解释的权利。</li>
        </ul>
      </div>
      <footer class="rule-footer">
        <div>填写收货地址&gt;&gt;</div>
      </footer>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Rule',
  data () {
    return {
      visible: false
    }
  },
  methods: {
    open () {
      this.visible = true
    },
    close () {
      this.visible = false
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
    overflow: auto;
    background-color: rgba(0,0,0,.86);
  }
  .rule-header{
    width: 100%;
    height : 1.7rem;
    margin: 3rem auto 0;
    background: url(../img/rule-header.png) no-repeat;
    background-size: 100% auto;
  }
  .rule-warp{
    width: 100%;
    background: url(../img/poster-bg.png) repeat-y;
    background-size: 100% auto;
  }
  .rule-list{
    width: 26.3rem;
    min-height: 10rem;
    margin: 0 auto;
    padding: 1.5rem 1rem;
    list-style: none;
    font-size: .9rem;
    
  }
  .rule-list li{
    text-align: justify;
  }
  .rule-footer{
    width: 100%;
    height : 1.76rem;
    margin: 0 auto 3rem;
    background: url(../img/rule-footer.png) no-repeat;
    background-size: 100% auto;
  }
  .rule-footer div{
    text-align: center;
    text-decoration-line: underline;
  }
</style>
