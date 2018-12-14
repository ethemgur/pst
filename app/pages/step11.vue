<template>
  <div data-page="step11" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a></div>
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
  created() {
    document.addEventListener('backbutton', this.onBackKeyDown, false)
    this.$db('bdi', 0)
    this.$db('satisfaction', 0)
    this.$db('selfesteem', 0)
    this.$db('spsi', 0)
    this.$db('stress', 0)
  },
  methods: {
    onBackKeyDown() {
      this.$f7.views.main.loadPage('/home/')
    },
    navigateURL() {
      this.$db('survey', 0)
      this.$f7.views.main.loadPage('/survey-spsi/0')
    },
  },
}
</script>
