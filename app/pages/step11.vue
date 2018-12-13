<template>
  <div data-page="step11" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">1. ADIM</div>
      </div>
    </div>
    <a class="floating-button color-purple" @click="navigateURL"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0; display: flex; align-items: center">
      <div class="card" style="border-radius: 20px; padding-top: 30px; padding-bottom: 30px">
        <div style="margin: 10px; text-align: center; font-size: 24px"> Şimdi sizden bazı testleri cevaplamanızı isteyeceğiz. Testlere başlamak için ilerleyin</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    navigateURL() {
      this.$db('survey', 0)
      this.$f7.views.main.loadPage('/survey-spsi/0')
    },
  },
}
</script>
