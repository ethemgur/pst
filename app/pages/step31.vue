<template>
  <div data-page="swiper-horizontal" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/" @click="pause" ><i class="icon icon-back"></i></a></div>
        <div class="center">{{title}}</div>
      </div>
    </div>
    <a :href="'step311' " class="floating-button color-purple" @click="pause"><i class="material-icons">navigate_next</i></a>

    <div class="page-content" style="background-color: #f0d2f0">
      <video class="video-content" width="300" controls id="videoElement" @canplay="updatePaused" @playing="updatePaused" @pause="updatePaused" style="border-radius: 20px">
        <source src="file:///android_asset/www/output12.mp4" type="video/mp4">
        </video>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: '3. AŞAMA',
      step: 0,
      videoElement: null,
      paused: null,
    }
  },
  created() {
    this.src = 'https://www.youtube-nocookie.com/embed/h29e6ciexvI'
    this.step = this.$route.params.step
    document.addEventListener('backbutton', this.onBackKeyDown, false)
  },
  methods: {
    onBackKeyDown() {
      this.pause()
      this.$f7.views.main.loadPage('/home/')
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
  computed: {
    playing() { return !this.paused },
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
}
</style>
