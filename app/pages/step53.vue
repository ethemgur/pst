<template>
  <div data-page="forms-checkboxes" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">{{$route.params.id}}</div>
      </div>
    </div>

    <a href="/step52/" class="floating-button color-cyan" @click="mergeChoices()"><i class="material-icons">navigate_next</i></a>

    <div class="page-content">
      <div class="content-block-title">Sorunu Çözmesi</div>
      <div class="list-block">
        <div class="item-content">
          <div class="item-media"><p>{{score1}}</p></div>
          <div class="item-inner">
            <div class="item-input">
              <div class="range-slider">
                <input v-model.number="score1" type="range" min="0" max="4" value="0" step="1">
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="content-block-title">Hedefle Uyumu</div>
      <div class="list-block">
        <div class="item-content">
          <div class="item-media"><p>{{score2}}</p></div>
          <div class="item-inner">
            <div class="item-input">
              <div class="range-slider">
                <input v-model.number="score2" type="range" min="0" max="4" step="0" value="4">
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="content-block-title">Uygulanabilirliği</div>
      <div class="list-block">
        <div class="item-content">
          <div class="item-media"><p>{{score3}}</p></div>
          <div class="item-inner">
            <div class="item-input">
              <div class="range-slider">
                <input v-model.number="score3" type="range" min="0" max="4" value="0" step="1">
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="content-block-title">Kabul edilebilirliği</div>
      <div class="list-block">
        <div class="item-content">
          <div class="item-media"><p>{{score4}}</p></div>
          <div class="item-inner">
            <div class="item-input">
              <div class="range-slider">
                <input v-model.number="score4" type="range" min="0" max="4" value="0" step="1">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      solutions: [],
      score1: 0,
      score2: 0,
      score3: 0,
      score4: 0,
    }
  },
  created() {
    if (localStorage.getItem('solutions')) {
      try {
        this.solutions = JSON.parse(localStorage.getItem('solutions'))
        console.log(`${this.solutions.length} solutions found in local storage!`)
      } catch (e) {
        console.log('Local Storage Error')
      }
    }
  },
  methods: {
    mergeChoices() {
      const scoresList = [this.score1, this.score2, this.score3, this.score4]
      this.solutions[this.getItemIndex(this.$route.params.id)].scores = scoresList
      const totalScore = this.score1 + this.score2 + this.score3 + this.score4
      this.solutions[this.getItemIndex(this.$route.params.id)].totalScore = totalScore
      localStorage.setItem('solutions', JSON.stringify(this.solutions))
      console.log('SOLUTION SCORES MERGED')
    },
    getItemIndex(text) {
      // eslint-disable-next-line no-restricted-syntax
      for (const r in this.solutions) {
        if (this.solutions[r].text === text) {
          return r
        }
      }
      return -1
    },
    saveSolutions() {
      localStorage.setItem('solutions', JSON.stringify(this.solutions))
    },
  },
}
</script>
