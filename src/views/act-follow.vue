<template>
  <div class="follow" v-show="visible">
    <div class="mask" @click='close'></div>
    <div class="follow__form">
      <div class="follow__form__bg"></div>
      <div class="follow__form__bg__mid">
        <header>
          {{nick}}
        </header>
        <div class="follow__form__content">
          <img src="../img/follow-head.png" />
          <div class="follow__form__content__input">
            <input v-model="number" type="number"/>
            <div @click="plus" class="btn btn__plus"></div>
            <div @click="minus" class="btn btn__minus"></div>
          </div>
        </div>
      </div>
      <footer @click="conform" class="follow__form__bg__end">
        <img src="../img/follow-btn.png" />
      </footer>
    </div>
  </div>
</template>
<script>
const numReg = /^[0-9]+$/
const numRe = new RegExp(numReg)
export default {
  name: 'Rule',
  data () {
    return {
      visible: true,
      nick: '我是主播的名字',
      id: '',
      number: 0
    }
  },
  created () {
    eventBus.$on('openFollow', obj => {
      this.nick = obj.nick
      this.id = obj.id
      this.visible = true
    })
  },
  methods: {
    close () {
      this.visible = false
    },
    plus () {
      if(numRe.test(this.number)) {
        this.number += 1
      } else {
        this.number = 1
      }
    },
    minus () {
      if(numRe.test(this.number) && this.number > 0) {
        this.number -= 1
      } else {
        this.number = 0
      }
    },
    conform () {
      eventBus.$emit('conformFollow', {'follow':this.number,'id':this.id})
      this.number = 0
      this.close()
    }
  }
}
</script>
