<template>
  <div data-page="step21" class="page toolbar-fixed kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left">
          <a class="link icon-only" href="/step211/"><i class="icon icon-back"></i></a>
        </div>
        <div class="center">Nedenler</div>
        <div class="right">
          <a class="link icon-only" href="#" @click="reasonPrompt"><i class="icon icon-plus"></i></a>
        </div>
      </div>
    </div>

    <a href="#" class="floating-button color-cyan" @click="navigateURL"><i class="material-icons">navigate_next</i></a>

      <div class="page-content">
        <div class="list-block">
          <ul>
            <li class="swipeout" v-for="i in reasons">
              <div class="item-content swipeout-content">
                <div class="item-inner">
                  <div class="item-title">{{i.text}}</div>
                </div>
              </div>
              <f7-swipeout-actions right>
                <f7-swipeout-button close @click="removeReason(i)" style="background-color:red">Delete</f7-swipeout-button>
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
      reasons: [],
    }
  },
  created() {
    if (localStorage.getItem('reasons')) {
      this.reasons = JSON.parse(localStorage.getItem('reasons'))
    } else {
      this.reasons = []
    }
  },
  methods: {
    reasonPrompt() {
      this.$f7.prompt('Yeni neden ekle', (data) => {
        if (data !== '') {
          this.reasons.push({
            text: data,
            match: [],
            scores: [],
            totalScore: 0,
          })
          this.saveReasons()
          console.log(`${data} is added!`)
        } else {
          this.reasonPrompt()
        }
      })
    },
    removeReason(value) {
      const index = this.reasons.indexOf(value)
      this.reasons.splice(index, 1)
      this.saveReasons()
    },
    saveReasons() {
      localStorage.setItem('reasons', JSON.stringify(this.reasons))
    },
    validation() {
      if (this.reasons.length === 0) {
        return false
      }
      return true
    },
    navigateURL() {
      if (this.validation()) {
        this.$f7.views.main.loadPage('/step22/')
        return
      }
      this.$f7.alert('Lütfen iki tabloyu doldurun.')
    },
  },

}
</script>
