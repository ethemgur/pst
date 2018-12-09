<template>
  <div data-page="step21" class="page toolbar-fixed kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left">
          <a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a>
        </div>
        <div class="center">Belirtiler</div>
        <div class="right">
          <a class="link icon-only" href="#" @click="symptomPrompt"><i class="icon icon-plus"></i></a>
        </div>
      </div>
    </div>

    <a href="#" class="floating-button color-cyan" @click="navigateURL"><i class="material-icons">navigate_next</i></a>

      <div class="page-content">
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
</template>

<script>

export default {
  data() {
    return {
      symptoms: [],
    }
  },
  created() {
    if (localStorage.getItem('symptoms') !== null) {
      this.symptoms = JSON.parse(localStorage.getItem('symptoms'))
    } else {
      this.symptoms = []
    }
    console.log(localStorage.getItem('symptoms') === null)
  },
  methods: {
    symptomPrompt() {
      this.$f7.prompt('Yeni belirti ekle', (data) => {
        if (data !== '') {
          this.symptoms.push({
            text: data,
          })
          this.saveSymptoms()
          console.log(`${data} is added!`)
        } else {
          this.symptomPrompt()
        }
      })
    },
    removeSymptom(value) {
      const index = this.symptoms.indexOf(value)
      this.symptoms.splice(index, 1)
      this.saveSymptoms()
    },
    saveSymptoms() {
      localStorage.setItem('symptoms', JSON.stringify(this.symptoms))
    },
    validation() {
      if (this.symptoms.length === 0) {
        return false
      }
      return true
    },
    navigateURL() {
      console.log('nextnav')
      if (this.validation()) {
        this.$f7.views.main.loadPage('/step212/')
        return
      }
      this.$f7.alert('Lütfen tabloyu doldurun.')
    },
  },

}
</script>
