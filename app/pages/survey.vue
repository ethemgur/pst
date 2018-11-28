<template>
  <div data-page="progressbar" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">TEST</div>
      </div>
    </div>

    <a :href="'/step' + step + '1/'" class="floating-button color-cyan""><i class="material-icons">navigate_next</i></a>

    <!-- SAYI INPUT 0-100 -->
    <div class="page-content">
      <div class="content-block">Bugün kendinizi ne kadar mutlu hissediyorsunuz?</div>
      <div class="content-block">
        <div class="list-block">
          <div class="item-content">
            <div class="item-media">{{score1}}</div>
            <div class="item-inner">
              <div class="item-input">
                <div class="range-slider">
                  <input v-model.number="score1" type="range" min="0" max="9" value="4" step="1">
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="content-block">Bugün kendinizi ne kadar seviyorsunuz?</div>
      <div class="content-block">
        <div class="list-block">
          <div class="item-content">
            <div class="item-media">{{score2}}</div>
            <div class="item-inner">
              <div class="item-input">
                <div class="range-slider">
                  <input v-model.number="score2" type="range" min="0" max="9" value="4" step="1">
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="content-block">Bugün kendinize ne kadar güveniyorsunuz?</div>
      <div class="content-block">
        <div class="list-block">
          <div class="item-content">
            <div class="item-media">{{score3}}</div>
            <div class="item-inner">
              <div class="item-input">
                <div class="range-slider">
                  <input v-model.number="score3" type="range" min="0" max="9" value="4" step="1">
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="content-block">Bugün kendinizi ne kadar tanıdığınızı hissediyorsunuz?</div>
      <div class="content-block">
        <div class="list-block">
          <div class="item-content">
            <div class="item-media">{{score4}}</div>
            <div class="item-inner">
              <div class="item-input">
                <div class="range-slider">
                  <input v-model.number="score4" type="range" min="0" max="9" value="4" step="1">
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <br />
      <br />
      <br />

    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      step: 0,
      score1: 0,
      score2: 0,
      score3: 0,
      score4: 0,

    }
  },
  created() {
    this.step = this.$route.params.step
  },
}
</script>
