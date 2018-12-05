<template>
  <div data-page="swiper-horizontal" class="page kitchen-sink-material">
    <!--div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">1. ADIM</div>
      </div>
    </div-->
    <div class="page-content">
      <div data-pagination=".swiper-pagination" data-paginationhide="true" class="swiper-container swiper-init ks-demo-slider">
        <div class="swiper-pagination"></div>
        <div class="swiper-wrapper">

          <div class="swiper-slide">

            <iframe width="300" src="file:///android_asset/www/cmylmz.mp4"></iframe>

          </div>

          <div class="swiper-slide">
            <a :href="'/survey/' + step" class="floating-button color-cyan""><i class="material-icons">navigate_next</i></a>
            <center>
              Şimdi sizden bazı soruları cevaplamanızı isteyeceğiz
            </center>
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
  mounted() {
  },
}
</script>
