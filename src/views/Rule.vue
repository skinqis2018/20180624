<template>
  <div class="component-rule" v-show="visible">
    <div class="mask" @click='close'>
      <header class="rule-header"></header>
      <div class="rule-warp">
        <ul class="rule-list">
          <li>1.活动时间为: 6月10日-6月18日</li>
          <li>2.主播战区划分:根据主播近30天开播最多品类自动分战区，战区不可调整。</li>
          <li>3.主播分级:根据5月流水排名, 1-15名为传说成员、16- 30名为超凡成员，31-50名为高手成员，其余主播为勇者成员。</li>
          <li>4.主播活动期间所有收到的钻石礼物按照价们自动换算成票数,其中普通礼物1钻石=1票，“狗东”礼物1个=50票，“大神奖章"1个=2票。BUFF礼物获取方法:直接购买+金卡传说专区兑换。</li>
          <li>5.主播奖励:人奖励:以活动期间主播日均人气值为计算基准，保底1w加成，最高加成不超过30w,其他牌面奖励将于活动结束后的7个工作日内人工联系发放。</li>
          <li>6.用户奖励:获得"618快递宝箱”中实物奖励的用户需在页面及时填写有效的联系方式，否则视为放弃奖励;获得最强粉丝奖励的用户，奖励将于7个工作日内发放至背包。</li>
          <li>7.腾讯公司保留法律范围内对活动规则进行解释的权利。</li>
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
