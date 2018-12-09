<template>
  <div data-page="step42" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left">
          <a class="back link icon-only" href="#"><i class="icon icon-back"></i></a>
        </div>
        <div class="center">Step 4</div>
      </div>
    </div>

    <div class="speed-dial">
      <a href="#" class="floating-button color-cyan"><i class="icon icon-plus"></i><i class="icon icon-close"></i></a>
      <div class="speed-dial-buttons">
        <a href="#" class="color-cyan" @click="solutionPrompt()"><i class="icon icon-plus"></i></a>
        <a class="color-cyan" @click="navigateURL"><i class="icon material-icons">navigate_next</i></a>
      </div>
    </div>

    <div class="page-content">
      <div class="content-block-title">Çözüm Belirleme</div>
      <div class="list-block">
        <ul>
          <li class="swipeout" v-for="i in solutions">
            <div class="item-content swipeout-content">
              <div class="item-inner">
                <div class="item-title">{{i.text}}</div>
              </div>
            </div>
            <f7-swipeout-actions right>
              <f7-swipeout-button close @click="removeSolution(i)" style="background-color:red">Delete</f7-swipeout-button>
            </f7-swipeout-actions>
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
    }
  },
  created() {
    if (localStorage.getItem('solutions')) {
      this.solutions = JSON.parse(localStorage.getItem('solutions'))
    } else {
      this.solutions = []
    }
  },
  methods: {
    solutionPrompt() {
      this.$f7.prompt('Yeni çözüm ekle', (data) => {
        if (data !== '') {
          this.solutions.push({
            text: data,
            scores: [],
            totalScore: 0,
            pp: [],
            pn: [],
            np: [],
            nn: [],
          })
          this.saveSolutions()
          console.log(`${data} is added!`)
        } else {
          this.solutionPrompt()
        }
      })
    },
    removeSolution(value) {
      const index = this.solutions.indexOf(value)
      this.solutions.splice(index, 1)
      this.saveSolutions()
    },
    saveSolutions() {
      localStorage.setItem('solutions', JSON.stringify(this.solutions))
    },
    validation() {
      if (this.solutions.length === 0) {
        return false
      }
      return true
    },
    navigateURL() {
      if (this.validation() && this.saveDB()) {
        this.$db('currentStep', 5)
        this.$f7.views.main.loadPage('/home/')
        return
      }
      this.$f7.alert('Lütfen tabloyu doldurun.')
    },
    saveDB() {
      if (!navigator.onLine) {
        window.f7.addNotification({
          title: 'Offline',
          message: 'This action is not possible in offline mode.',
          hold: 3000,
          closeIcon: false,
        })
        return false
      }
      let saved = false
      setTimeout(() => {
        if (!saved) {
          this.$f7.showIndicator()
        }
      }, 1000)
      // eslint-disable-next-line no-restricted-syntax
      for (const r in this.solutions) {
        const el = this.solutions[r]

        window.db(`users/${this.$user.uid}/solutions`)
          .child(el.text).set({
            text: el.text,
            scores: el.scores,
            totalScore: el.totalScore,
            pp: el.pp,
            pn: el.pn,
            np: el.np,
            nn: el.nn,
          })
          .then(() => {
          })
          .catch(() => {
            this.$f7.alert('Cannot save new task :-(<br />Please try again later', 'Trouble with Firebase')
            this.$f7.hideIndicator()
            return false
          })
      }

      window.db(`users/${this.$user.uid}`)
        .child('currentStep').set({
          step: 5,
        })
        .then(() => {
          saved = true
          this.$f7.hideIndicator()
        })
        .catch(() => {
          this.$f7.alert('Cannot save new task :-(<br />Please try again later', 'Trouble with Firebase')
          saved = true
          this.$f7.hideIndicator()
          return false
        })
      return true
    },
  },

}
</script>
