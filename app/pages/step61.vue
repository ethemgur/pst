<template>
  <div data-page="swiper-horizontal" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#" @click="pause"><i class="icon icon-back"></i></a></div>
        <div class="center">{{title}}</div>
      </div>
    </div>
    <a class="floating-button color-purple" @click="navigateURL"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0">
      <video class="video-content" width="300" controls id="videoElement" @canplay="updatePaused" @playing="updatePaused" @pause="updatePaused" style="border-radius: 20px">
        <source src="file:///android_asset/www/output19.mp4" type="video/mp4" />
      </video>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: '6. AŞAMA',
      videoElement: null,
      paused: null,
    }
  },
  created() {
    document.addEventListener('backbutton', this.onBackKeyDown, false)
  },
  methods: {
    onBackKeyDown() {
      this.pause()
      this.$f7.views.main.loadPage('/home/')
    },
    navigateURL() {
      console.log('navigate')
      try {
        this.pause()
      } catch (e) {
        console.log(e)
      }
      this.$f7.views.main.loadPage('/step611/')
    },
    updatePaused(event) {
      this.videoElement = event.target
      this.paused = event.target.paused
    },
    play() {
      this.videoElement.play()
    },
    pause() {
      this.videoElement.pause()
    },
  },
}
</script>

<style media="screen">
.video-content
{
  position: absolute;
  margin: auto;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  width: 95%;
  border-radius: 3px;
}
</style>
