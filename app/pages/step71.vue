<template>
  <div data-page="step21" class="page toolbar-fixed kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left">
          <a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a>
        </div>
        <div class="center">Plan Aşamaları</div>
        <div class="right">
          <a class="link icon-only" href="#" @click="planPrompt"><i class="icon icon-plus"></i></a>
        </div>
      </div>
    </div>

    <a :href="navigateURL()" class="floating-button color-cyan" @click="validationAlert"><i class="material-icons">navigate_next</i></a>

      <div class="page-content">
        <div class="list-block">
          <ul>
            <span v-for="i in plans">
            <div class="content-block-title">
              {{plans.indexOf(i) + 1}}. Aşama
            </div>
            <li class="swipeout">
              <div class="item-content swipeout-content">
                <div class="item-inner">
                  <div class="item-title">{{i.text}}</div>
                </div>
              </div>
              <f7-swipeout-actions right>
                <f7-swipeout-button close @click="removePlan(i)" style="background-color:red">Delete</f7-swipeout-button>
              </f7-swipeout-actions>
            </li>
          </span>
          </ul>
        </div>
      </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      plans: [],
    }
  },
  created() {
    if (localStorage.getItem('plans')) {
      this.plans = JSON.parse(localStorage.getItem('plans'))
    } else {
      this.plans = []
    }
  },
  methods: {
    planPrompt() {
      this.$f7.prompt('Yeni aşama ekle', (data) => {
        if (data !== '') {
          this.plans.push({
            id: data,
            text: data,
          })
          this.savePlans()
          console.log(`${data} is added!`)
        } else {
          this.planPrompt()
        }
      })
    },
    removePlan(value) {
      const index = this.plans.indexOf(value)
      this.plans.splice(index, 1)
      this.savePlans()
    },
    savePlans() {
      localStorage.setItem('plans', JSON.stringify(this.plans))
    },
    validation() {
      if (this.plans.length === 0) {
        return false
      }
      return true
    },
    navigateURL() {
      if (this.validation()) {
        return '/step72/'
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
