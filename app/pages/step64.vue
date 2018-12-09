<template>
  <div data-page="step61" class="page toolbar-fixed kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left">
          <a class="back link icon-only" href="#"><i class="icon icon-back"></i></a>
        </div>
        <div class="center">Step 6</div>
        <div class="right">
          <a class="link icon-only" href="#" @click="solutionPrompt"><i class="icon icon-plus"></i></a>
        </div>
      </div>
    </div>

    <a class="floating-button color-cyan" @click="navigateURL"><i class="material-icons">navigate_next</i></a>

    <div class="page-content">
      <div class="content-block-title">
        {{solution.text}}
        <br />
        <br />
        Çözümünü uygulamamanın olumsuz sonuçları
      </div>
      <div class="list-block">
        <ul>
          <li class="swipeout" v-for="i in items">
            <div class="item-content swipeout-content">
              <div class="item-inner">
                <div class="item-title">{{i}}</div>
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
      solution: {},
      items: [],
    }
  },

  created() {
    this.solution = this.$db('bestSolution')
    this.items = this.solution.nn
  },

  methods: {
    solutionPrompt() {
      this.$f7.prompt('Yeni sonuç ekle', (data) => {
        if (data !== '') {
          this.items.push(data)
          console.log(`${data} is added!`)
          this.saveSolution()
        } else {
          this.solutionsPrompt()
        }
      })
    },
    removeSolution(value) {
      const index = this.items.indexOf(value)
      this.items.splice(index, 1)
      this.saveSolutions()
    },
    saveSolution() {
      this.solution.nn = this.items
      this.$db('bestSolution', this.solution)
    },
    validation() {
      if (this.items.length === 0) {
        return false
      }
      return true
    },
    navigateURL() {
      this.saveSolution()
      if (this.saveDB() && this.validation()) {
        this.$f7.views.main.loadPage('/step65/')
      }
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

      // Show loading indicator with delay
      let saved = false
      const el = this.solution
      setTimeout(() => {
        if (!saved) {
          this.$f7.showIndicator()
        }
      }, 1000)
      window.db(`users/${this.$user.uid}`)
        .child('bestSolution').set({
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

      window.db(`users/${this.$user.uid}`)
        .child('currentStep').set({
          step: 7,
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
