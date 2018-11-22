<template>
  <div data-page="step21" class="page kitchen-sink-material">
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
        <a :href="navigateURL()" class="color-cyan" @click="validationAlert()"><i class="icon material-icons">navigate_next</i></a>
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
            id: data,
            text: data,
            scores: [],
            totalScore: 0,
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
      if (this.validation()) {
        return '/home/'
      }
      return '#'
    },
    validationAlert() {
      if (!this.validation()) {
        this.$f7.alert('Lütfen tabloyu doldurun.')
      }
    },
  },

}
</script>
