<template>
  <div data-page="step22" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left">
          <a class="back link icon-only" href="#"><i class="icon icon-back"></i></a>
        </div>
        <div class="center">Step 2-2</div>
      </div>
    </div>
    <a v-show="!isCompleted()" href="#" class="floating-button" style="background:grey"><i class="material-icons">navigate_next</i></a>
    <a v-show="isCompleted()" href="/step24/" class="floating-button color-cyan"><i class="material-icons">navigate_next</i></a>
    <div class="page-content">
      <div class="content-block-title">Nedenlere tıklayarak uygun belirtileri seçin</div>
      <div class="list-block">
        <ul>
          <li v-for="i in reasons">
            <a :href="'/step23/' + i.id" class="item-link item-content">
              <div class="item-inner">
                <div class="item-title">{{i.text}}</div>
                <div class="item-after item-media"><i v-show="isReasonMatched(i)" class="icon material-icons color-cyan">done</i></div>
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
    console.log(this.reasons)
  },

  methods: {
    isCompleted() {
      // eslint-disable-next-line no-restricted-syntax
      for (const r in this.reasons) {
        if (this.reasons[r].match.length === 0) {
          return false
        }
      }
      return true
    },
    isReasonMatched(r) {
      return r.match.length !== 0
    },
  },

}
</script>
