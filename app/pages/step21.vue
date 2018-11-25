<template>
  <div data-page="step21" class="page toolbar-fixed kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left">
          <a class="back link icon-only" href="#"><i class="icon icon-back"></i></a>
        </div>
        <div class="center">Step 2-1</div>
        <div class="right">
          <a class="link icon-only" href="#" @click="promptSelector"><i class="icon icon-plus"></i></a>
        </div>
      </div>
    </div>

    <div class="toolbar tabbar">
      <div class="toolbar-inner">
        <a href="#tab1" class="active tab-link" v-on:click="tabChange(1)">NEDENLER</a>
        <a href="#tab2" class="tab-link" v-on:click="tabChange(2)">BELİRTİLER</a>
      </div>
    </div>

    <a href="#" class="floating-button color-cyan" @click="validationAlert"><i class="material-icons">navigate_next</i></a>

    <div class="tabs">
      <div id="tab1" class="page-content tab active">
        <div class="list-block">
          <ul>
            <li class="swipeout" v-if="current_tab === 1" v-for="i in reasons">
              <div class="item-content swipeout-content">
                <div class="item-inner">
                  <div class="item-title">{{i.text}}</div>
                </div>
              </div>
              <f7-swipeout-actions right>
                <f7-swipeout-button close @click="removeReason(i)" style="background-color:red">Delete</f7-swipeout-button>
              </f7-swipeout-actions>
            </li>
            <li class="swipeout" v-if="current_tab === 2" v-for="i in symptoms">
              <div class="item-content swipeout-content">
                <div class="item-inner">
                  <div class="item-title">{{i.text}}</div>
                </div>
              </div>
              <f7-swipeout-actions right>
                <f7-swipeout-button close @click="removeSymptom(i)" style="background-color:red">Delete</f7-swipeout-button>
              </f7-swipeout-actions>
            </li>
          </ul>
        </div>
      </div>
      <div id="tab2" class="page-content tab">
        <div class="list-block">
          <ul>
            <li class="swipeout" v-for="i in symptoms">
              <div class="item-content swipeout-content">
                <div class="item-inner">
                  <div class="item-title">{{i.text}}</div>
                </div>
              </div>
              <f7-swipeout-actions right>
                <f7-swipeout-button close @click="removeSymptom(i)" style="background-color:red">Delete</f7-swipeout-button>
              </f7-swipeout-actions>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      current_tab: 1,
      reasons: [],
      symptoms: [],
    }
  },
  created() {
    if (localStorage.getItem('reasons')) {
      this.reasons = JSON.parse(localStorage.getItem('reasons'))
    } else {
      this.reasons = []
    }

    if (localStorage.getItem('symptoms')) {
      this.symptoms = JSON.parse(localStorage.getItem('symptoms'))
    } else {
      this.symptoms = []
    }
  },
  methods: {
    reasonPrompt() {
      this.$f7.prompt('Yeni neden ekle', (data) => {
        if (data !== '') {
          this.reasons.push({
            id: data,
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
    symptomPrompt() {
      this.$f7.prompt('Yeni belirti ekle', (data) => {
        if (data !== '') {
          this.symptoms.push({
            id: data,
            text: data,
          })
          this.saveSymptoms()
          console.log(`${data} is added!`)
        } else {
          this.symptomPrompt()
        }
      })
    },
    removeReason(value) {
      const index = this.reasons.indexOf(value)
      this.reasons.splice(index, 1)
      this.saveReasons()
    },
    removeSymptom(value) {
      const index = this.symptoms.indexOf(value)
      this.symptoms.splice(index, 1)
      this.saveSymptoms()
    },
    saveReasons() {
      localStorage.setItem('reasons', JSON.stringify(this.reasons))
    },
    saveSymptoms() {
      localStorage.setItem('symptoms', JSON.stringify(this.symptoms))
    },
    promptSelector() {
      if (this.current_tab === 1) {
        return this.reasonPrompt()
      }
      return this.symptomPrompt()
    },
    validation() {
      if (this.reasons.length * this.symptoms.length === 0) {
        return false
      }
      return true
    },
    navigateURL() {
      if (this.validation()) {
        return '/step22/'
      }
      return '#'
    },
    validationAlert() {
      if (!this.validation()) {
        this.$f7.alert('Lütfen iki tabloyu da doldurun.')
      }
    },
    tabChange(tab) {
      this.current_tab = tab
    },
  },

}
</script>
