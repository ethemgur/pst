<template>
  <div data-page="video" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">6. ADIM</div>
      </div>
    </div>
    <a :href=" '/step41/' " class="floating-button color-purple"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0">
      <div class= content>
        <div class="card" style="border-radius: 20px">
          <video class="video-content" width="300" controls id="videoElement" @canplay="updatePaused" @playing="updatePaused" @pause="updatePaused" style="border-radius: 20px">
            <source src="file:///android_asset/www/output22.mp4" type="video/mp4">
          </video>
        </div>
      </div>
    </div>
  </div>
</template>
<style media="screen">
  .content{
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    width: 90%;
    margin-right: -50%;
    transform: translate(-50%, -50%)
  }
  .text{
    text-align: center;

  }
</style>

<script>
export default {
  methods: {
    navigateURL() {
      this.$db('currentStep', 4)
      this.$f7.views.main.loadPage('/step42/')
    },
  },
}
</script>
