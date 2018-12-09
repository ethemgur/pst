<template>
  <div data-page="step23" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/step22/"><i class="icon icon-back"></i></a></div>
        <div class="center">Step 2-3</div>
      </div>
    </div>
    <a href="/step22/" class="floating-button color-cyan" @click="matchChoices()"><i class="material-icons">navigate_next</i></a>
    <div class="page-content">
      <div class="content-block-title">Uygun gördüğünüz belirtileri seçin:</div>
      <div class="list-block">
        <ul>
          <li v-for="i in symptoms">
            <label class="label-checkbox item-content">
              <input v-model="checkedSymptoms" type="checkbox" name="ks-checkbox" :value="i">
              <div class="item-media"><i class="icon icon-form-checkbox"></i></div>
              <div class="item-inner">
                <div class="item-title">{{i.text}}</div>
              </div>
            </label>
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
      symptoms: [],
      checkedSymptoms: [],
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

    if (localStorage.getItem('symptoms')) {
      try {
        this.symptoms = JSON.parse(localStorage.getItem('symptoms'))
        console.log(`${this.symptoms.length} symptoms found in local storage!`)
      } catch (e) {
        console.log('Local Storage Error')
      }
    }
  },

  methods: {
    matchChoices() {
      this.reasons[this.getItemIndex(this.$route.params.id)].match = this.checkedSymptoms
      localStorage.setItem('reasons', JSON.stringify(this.reasons))
    },
    getItemIndex(text) {
      // eslint-disable-next-line no-restricted-syntax
      for (const r in this.reasons) {
        if (this.reasons[r].text === text) {
          return r
        }
      }
      return -1
    },
  },
}
</script>
