<template>
  <div data-page="step24" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">Step 2-4</div>
      </div>
    </div>

    <a v-show="!isCompleted()" href="#" class="floating-button" style="background:grey"><i class="material-icons">navigate_next</i></a>
    <a v-show="isCompleted() && isOrdered" href="/home/" class="floating-button color-cyan" @click="saveDB"><i class="material-icons">navigate_next</i></a>
    <a v-show="isCompleted() && !isOrdered" href="/step24/" class="floating-button color-cyan" @click="orderReasons()"><i class="material-icons">navigate_next</i></a>

    <div class="page-content">
      <div class="content-block-title">Nedenlere tıklayarak derecenlendirin</div>
      <div class="list-block">
        <ul>
          <li v-for="i in reasons">
            <a :href="'/step25/' + i.id" class="item-link item-content">
              <div class="item-inner">
                <div class="item-title">{{i.text}}</div>
                <div v-show="isReasonMatched(i)" class="item-after item-media"> {{i.totalScore}} <i class="icon material-icons color-cyan">done</i></div>
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
      reasons: [],
      isOrdered: false,
    }
  },

  created() {
    if (localStorage.getItem('reasons')) {
      try {
        this.reasons = JSON.parse(localStorage.getItem('reasons'))
        console.log(`${this.reasons.length} reasons found in local storage!`)
      } catch (e) {
        console.log('Local Storage Error')
      }
    }
  },

  methods: {
    isCompleted() {
      // eslint-disable-next-line no-restricted-syntax
      for (const r in this.reasons) {
        if (this.reasons[r].scores.length === 0) {
          return false
        }
      }
      return true
    },
    isReasonMatched(r) {
      return r.scores.length === 3
    },
    orderReasons() {
      const orderedReasons = []
      const reasons = this.reasons.slice()

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
      this.reasons = orderedReasons.reverse()
      this.isOrdered = true
      this.$f7.alert('Nedenler verilen puanlara göre sıralandı.')
    },
    saveDB() {
      if (!navigator.onLine) {
        window.f7.addNotification({
          title: 'Offline',
          message: 'This action is not possible in offline mode.',
          hold: 3000,
          closeIcon: false,
        })
        return
      }

      // eslint-disable-next-line no-restricted-syntax
      for (const r in this.reasons) {
        // Show loading indicator with delay
        let saved = false
        const el = this.reasons[r]
        setTimeout(() => {
          if (!saved) {
            this.$f7.showIndicator()
          }
        }, 1000)
        window.db('user/reasons')
          .child(el.id).set({
            text: el.text,
            match: el.match,
            scores: el.scores,
            totalScore: el.totalScore,
          })
          .then(() => {
            saved = true
            this.$f7.hideIndicator()
          })
          .catch(() => {
            this.$f7.alert('Cannot save new task :-(<br />Please try again later', 'Trouble with Firebase')
            saved = true
            this.$f7.hideIndicator()
          })
      }
    },
  },

}
</script>
