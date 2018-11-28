<template>
  <div data-page="list-view" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">Çözüm Çizelgesi</div>
      </div>
    </div>

    <a v-show="isCompleted()" href="/home/" class="floating-button color-cyan"><i class="material-icons">navigate_next</i></a>

    <a v-show="!isCompleted()" href="#" class="floating-button" style="background:grey" @click="validationAlert()"><i class="material-icons">navigate_next</i></a>
    <a v-show="isCompleted() && isOrdered" href="/home/" class="floating-button color-cyan" @click=""><i class="material-icons">navigate_next</i></a>
    <a v-show="isCompleted() && !isOrdered" href="/step52/" class="floating-button color-cyan" @click="orderReasons()"><i class="material-icons">navigate_next</i></a>

    <div class="page-content">
      <div class="content-block-title">Çözüm Önerileri</div>
      <div class="list-block">
        <ul>
          <li v-for="i in solutions">
            <a :href="'/step53/' + i.id" class="item-link item-content">
              <div class="item-inner">
                <div class="item-title">{{i.text}}</div>
                <div v-show="isSolutionMatched(i)" class="item-after item-media">
                  {{i.totalScore}}
                  <i class="icon material-icons color-cyan">done</i>
                </div>
              </div>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      solutions: [],
      isOrdered: false,
    }
  },
  created() {
    if (localStorage.getItem('solutions')) {
      try {
        this.solutions = JSON.parse(localStorage.getItem('solutions'))
        console.log(`${this.solutions.length} solutions found in local storage!`)
      } catch (e) {
        console.log('Local Storage Error')
      }
    }
  },
  methods: {
    isCompleted() {
      // eslint-disable-next-line no-restricted-syntax
      for (const s in this.solutions) {
        if (this.solutions[s].scores.length === 0) {
          return false
        }
      }
      return true
    },
    validationAlert() {
      if (!this.isCompleted()) {
        this.$f7.alert('Lütfen tabloyu doldurun.')
      }
    },
    isSolutionMatched(s) {
      return s.scores.length === 4
    },
    orderReasons() {
      const orderedReasons = []
      const reasons = this.solutions.slice()

      while (reasons.length > 0) {
        let min = 99999
        let minIndex = 0
        // eslint-disable-next-line no-restricted-syntax
        for (const r in reasons) {
          if (reasons[r].totalScore <= min) {
            min = reasons[r].totalScore
            minIndex = r
          }
        }
        orderedReasons.push(reasons[minIndex])
        reasons.splice(minIndex, 1)
      }
      this.solutions = orderedReasons.reverse()
      this.isOrdered = true
      this.$db('bestSolutionID', 0)
      this.$f7.alert('Çözümler verilen puanlara göre sıralandı.')
    },
  },
}
</script>
