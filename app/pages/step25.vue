<template>
  <div data-page="forms-checkboxes" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/step24/"><i class="icon icon-back"></i></a></div>
        <div class="center">{{el.text}}</div>
      </div>
    </div>
    <div class="page-content">

      <a href="/step24/" class="floating-button color-cyan" @click="mergeChoices()"><i class="material-icons">navigate_next</i></a>

      <div class="content-block">Bu nedenin şikayetlerinize olan katkısı?</div>
      <div class="list-block">
        <div class="item-content">
          <div class="item-media"><p>{{score1}}</p></div>
          <div class="item-inner">
            <div class="item-input">
              <div class="range-slider">
                <input v-model.number="score1" type="range" min="0" max="9" value="4" step="1">
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="content-block">Eğer bu nedeni kaldırırsak şikayetleriniz ne kadar azalır?</div>
      <div class="list-block">
        <div class="item-content">
          <div class="item-media"><p>{{score2}}</p></div>
          <div class="item-inner">
            <div class="item-input">
              <div class="range-slider">
                <input v-model.number="score2" type="range" min="0" max="9" step="1" value="4">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      reasons: [],
      el: {},
      score1: 0,
      score2: 0,
      score3: 0,
    }
  },

  created() {
    if (localStorage.getItem('reasons')) {
      try {
        this.reasons = JSON.parse(localStorage.getItem('reasons'))
        console.log(`${this.reasons.length} reasons found in local storage!`)
        this.el = this.reasons[this.getItemIndex(this.$route.params.id)]
      } catch (e) {
        console.log('Local Storage Error')
      }
    }
  },

  methods: {
    mergeChoices() {
      const scoresList = [this.score1, this.score2, this.score3]
      this.reasons[this.getItemIndex(this.$route.params.id)].scores = scoresList
      const totalScore = this.score1 + this.score2 + this.score3
      this.reasons[this.getItemIndex(this.$route.params.id)].totalScore = totalScore
      localStorage.setItem('reasons', JSON.stringify(this.reasons))
    },
    getItemIndex(id) {
      // eslint-disable-next-line no-restricted-syntax
      for (const r in this.reasons) {
        if (this.reasons[r].id === id) {
          return r
        }
      }
      return -1
    },
  },

}
</script>
