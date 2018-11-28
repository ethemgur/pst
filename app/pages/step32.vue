<template>
  <div data-page="step32" class="page toolbar-fixed kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left">
          <a class="back link icon-only" href="#"><i class="icon icon-back"></i></a>
        </div>
        <div class="center">Step 3</div>
      </div>
    </div>

    <a href="/step33/" v-show="validation()" class="floating-button color-cyan" @click="saveGoals()"><i class="material-icons">navigate_next</i></a>
    <a href="#" v-show="!validation()" class="floating-button" @click="validationAlert()" style="background:grey"><i class="material-icons">navigate_next</i></a>

    <div class="page-content">
      <div class="content-block-title"><center>{{bestReason.text}}</center></div>
      <form class="list-block inputs-list">
        <ul>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons">label_outline</i></div>
              <div class="item-inner">
                <div class="item-title floating-label">Hedef</div>
                <div class="item-input">
                  <input v-model="goal1" type="text" placeholder="">
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons">label_outline</i></div>
              <div class="item-inner">
                <div class="item-title floating-label">Hedef</div>
                <div class="item-input">
                  <input v-model="goal2" type="text" placeholder="">
                </div>
              </div>
            </div>
          </li>
        </ul>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      reasons: [],
      goal1: '',
      goal2: '',
      bestReason: {},
    }
  },

  mounted() {
    if (localStorage.getItem('reasons')) {
      try {
        this.reasons = JSON.parse(localStorage.getItem('reasons'))
        console.log(`${this.reasons.length} reasons found in local storage!`)
      } catch (e) {
        console.log('Local Storage Error')
      }
    }

    this.getBestReason()
  },

  methods: {
    getBestReason() {
      let totalScore = 0
      let bestReason = {}
      // eslint-disable-next-line no-restricted-syntax
      for (const r in this.reasons) {
        const reason = this.reasons[r]
        if (reason.totalScore > totalScore) {
          totalScore = reason.totalScore
          bestReason = reason
        }
      }
      this.bestReason = bestReason
    },
    saveGoals() {
      const goals = [this.goal1, this.goal2]
      localStorage.setItem('goals', JSON.stringify(goals))
    },
    validation() {
      const val1 = this.goal1.length !== 0 // || !this.goal1.trim()
      const val2 = this.goal2.length !== 0 // || !this.goal2.trim()
      return (val1 || val2)
    },
    validationAlert() {
      if (!this.validation()) {
        this.$f7.alert('Lütfen 2 adet hedef girin.')
      }
    },
  },
}
</script>
