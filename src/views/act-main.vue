<template>
  <div>
    <div v-if="isAnchors" class="anchors">
      <div class="anchors__head">
        <div class="anchors__head__text">
          1x&nbsp;
          <img class="anchors__head__rose" src="../img/rose.png" />
          =1积分
        </div>
        <img @click="toTask" src="../img/get_count.png"/>
      </div>
      <div class="anchors__list">
        <div class="anchors__list__head">
          <div class="anchors__list__head__left">评选第01期提名主播</div>
          <div class="anchors__list__head__right" @click="change">评选第01期十佳视频</div>
        </div>
        <div class="anchors__list__content">
          <div>
            <div>排名</div>
            <div>主播昵称</div>
            <div class="anchors__list__content__count">积分</div>
          </div>
          <div class="line"></div>
          <ul>
            <li 
              v-for="item in anchors[0]"
              :key="item.ranking">
              <p class="anchors__list__content__ranking">{{item.ranking}}</p>
              <div class="anchors__list__content__nick">
                <div 
                  class="anchors__list__content__avatar"
                  :class="{ anchors__list__content__avatar__first: item.ranking == 1,
                    anchors__list__content__avatar__second: item.ranking == 2,
                    anchors__list__content__avatar__third: item.ranking == 3,
                    anchors__list__content__avatar__normal: item.ranking > 3}">
                  <img src="../img/avatar.jpeg" />
                </div>
                <span>{{item.nick}}</span>
              </div>
              <p class="anchors__list__content__score">{{item.score}}</p>
            </li>
          </ul>
        </div>
        <div class="anchors__list__foot">
          <div class="anchors__list__foot__mark">
            <img 
              src="../img/lt.png"
              @click="changePage('pre')">
            <span 
              :class="{ activePage: currentPage == 1}"
              @click="changePage(1)">
              1
            </span>
            <span>|</span>
            <span 
              :class="{ activePage: currentPage == 2}"
              @click="changePage(2)">
              2
            </span>
            <span>|</span>
            <span 
              :class="{ activePage: currentPage == 3}"
              @click="changePage(3)">
              3
            </span>
            <img 
              src="../img/gt.png"
              @click="changePage('next')">
          </div>
        </div>
      </div>
      <div class="anchors__task">
        <img class="anchors__task__banner" src="../img/task-banner.png"/>
        <div class="anchors__task__items">
          <img src="../img/task1.png">
          <img src="../img/task2.png">
          <img src="../img/task3.png">
          <img src="../img/task4.png">
        </div>
        <div class="anchors__task__btn">
          <img src="../img/task-btn2.png">
          <img src="../img/task-btn1.png">
          <img src="../img/task-btn1.png">
          <img src="../img/task-btn1.png">
        </div>
        <div class="anchors__task__rule">
          注:好友登录奖励需要好友是未登录过企鹅电竞的新用户或超过2周没有登陆的老用户，通过您的分享登陆企鹅电竞,您将额外获得3000个玫瑰花。
        </div>
      </div>
    </div>
    <div v-else class="videos">
      <div class="videos__head">
        <div class="videos__head__detail">
          <div>点击
            <img src="../img/follow.png">
            ，评选出本周“十大人物”和十佳视频</div>
          <div>
            今日点赞机会还剩:{{count}}次
            <img @click="count--" src="../img/refresh.png">
          </div>
        </div>
        <img @click="toTask" src="../img/get_count.png" />
      </div>
      <div class="videos__list">
        <div class="videos__list__head">
          <div class="videos__list__head__left" @click="change">评选第01期提名主播</div>
          <div class="videos__list__head__right">评选第01期十佳视频</div>
        </div>
        <div class="videos__list__content">
          <div class="videos__list__content__box">
            <div 
              v-for="item in videos[0]" 
              :key="item.id"
              class="videos__list__content__item">
              <div class="videos__list__content__item__poster">
                <img src="../img/poster.jpeg">
              </div>
              <div class="videos__list__content__item__detail">
                <div class="videos__list__content__item__detail__avatar">
                  <img src="../img/avatar.jpeg">
                </div>
                <div class="videos__list__content__item__detail__nick">
                  {{item.nick}}
                </div>
                <div @click="openFollow(item.nick, item.id)" class="videos__list__content__item__detail__follow">
                  <img src="../img/follow.png">
                  {{item.follow}}
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="anchors__list__foot">
          <div class="anchors__list__foot__mark">
            <img 
              src="../img/lt.png"
              @click="changeVideoPage('pre')">
            <span 
              :class="{ activePage: currentVideoPage == 1}"
              @click="changeVideoPage(1)">
              1
            </span>
            <span>|</span>
            <span 
              :class="{ activePage: currentVideoPage == 2}"
              @click="changeVideoPage(2)">
              2
            </span>
            <span>|</span>
            <span 
              :class="{ activePage: currentVideoPage == 3}"
              @click="changeVideoPage(3)">
              3
            </span>
            <img 
              src="../img/gt.png"
              @click="changeVideoPage('next')">
          </div>
        </div>
      </div>
      <div class="anchors__task">
        <img class="anchors__task__banner" src="../img/task-banner.png"/>
        <div class="anchors__task__items">
          <img src="../img/video-task1.png">
          <img src="../img/video-task2.png">
          <img src="../img/video-task3.png">
          <img src="../img/video-task4.png">
        </div>
        <div class="anchors__task__btn">
          <img src="../img/task-btn2.png">
          <img src="../img/task-btn1.png">
          <img src="../img/task-btn1.png">
          <img src="../img/task-btn1.png">
        </div>
        <div class="anchors__task__rule">
          注:好友登录奖励需要好友是未登录过企鹅电竞的新用户或超过2周没有登陆的老用户，通过您的分享登陆企鹅电竞，您将额外获得50次点赞机会。
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      isAnchors: true,
      currentPage: 1,
      currentVideoPage: 1,
      count: 9999,
      anchors: [
        [
          {
            ranking: 1,
            avatar: '',
            nick: '我是主播的名称',
            score: 9999999
          },{
            ranking: 2,
            avatar: '',
            nick: '我是我是我是我是我是',
            score: 999999999999
          },{
            ranking: 3,
            avatar: '',
            nick: '我是',
            score: 9
          },{
            ranking: 4,
            avatar: '',
            nick: '我',
            score: 99
          },{
            ranking: 5,
            avatar: '',
            nick: '我是主播的',
            score: 999
          },{
            ranking: 6,
            avatar: '',
            nick: '我是主播',
            score: 9999
          },{
            ranking: 7,
            avatar: '',
            nick: '我',
            score: 99999
          },{
            ranking: 8,
            avatar: '',
            nick: '我',
            score: 19
          },{
            ranking: 9,
            avatar: '',
            nick: '我',
            score: 9
          },{
            ranking: 10,
            avatar: '',
            nick: '我',
            score: 9
          }
        ]
      ],
      videos: [
        [
          {
            id: 0,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播名字',
            follow: 9999
          },{
            id: 1,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播的名字',
            follow: 9999
          },{
            id: 2,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播得的名字',
            follow: 9999
          },{
            id: 3,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播名字',
            follow: 999
          },{
            id: 4,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播名字',
            follow: 999
          },{
            id: 5,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播名字',
            follow: 999
          },{
            id: 6,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播名字',
            follow: 9999
          },{
            id: 7,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播名字',
            follow: 9
          },{
            id: 8,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播名字',
            follow: 99
          },{
            id: 9,
            poster: '',
            avatar: '/img/avatar.jpeg',
            nick: '我是主播名字',
            follow: 999
          }
        ]
      ]
    }
  },
  created () {
    eventBus.$on('conformFollow', obj => {
      this.videos[0].map(item => {
        if(item.id == obj.id) {
          item.follow += obj.follow
        }
      })
    })
  },
  methods: {
    change () {
      this.currentVideoPage = 1
      this.currentPage = 1
      this.isAnchors = !this.isAnchors
    },
    changePage (val) {
      if (Number.isInteger(val)&&this.currentPage != val) {
        this.currentPage = val
      } else if (val == 'pre' && this.currentPage != 1) {
        this.currentPage--
      } else if (val == 'next' && this.currentPage != 3) {
        this.currentPage++
      }
    },
    changeVideoPage (val) {
      if (Number.isInteger(val)&&this.currentVideoPage != val) {
        this.currentVideoPage = val
      } else if (val == 'pre' && this.currentVideoPage != 1) {
        this.currentVideoPage--
      } else if (val == 'next' && this.currentVideoPage != 3) {
        this.currentVideoPage++
      }
    },
    openFollow (nick, id) {
      eventBus.$emit('openFollow', {'nick':nick,'id':id})
    },
    toTask () {
      let task = document.getElementsByClassName('anchors__task')[0]
      if (task) {
        let total = task.offsetTop
        document.body.scrollTop = total
        document.documentElement.scrollTop = total
        window.pageYOffset = total
      }
    }
  }
}
</script>

