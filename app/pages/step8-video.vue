<template>
  <div data-page="swiper-horizontal" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/" @click="pause2" ><i class="icon icon-back"></i></a></div>
        <div class="center">{{title}}</div>
      </div>
    </div>
    <a href="/step83/" class="floating-button color-purple" @click="pause2"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0">
      <iframe id="yvideo" class="video-content" :src="src" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      src: '',
      title: 'Step 8',
      step: 0,
      videoElement: null,
      paused: null,
    }
  },
  created() {
    this.src = `https://www.youtube-nocookie.com/embed/${this.videoName()}`
    this.step = this.$route.params.step
    document.addEventListener('backbutton', this.onBackKeyDown, false)
  },
  methods: {
    pause2() {
      this.src = ''
    },
    onBackKeyDown() {
      this.pause()
      this.$f7.views.main.loadPage('/home/')
    },
    videoName() {
      if (this.$db('step81-ans') === 'Evet') {
        return 'WY9FV-t03m8'
      }
      return '_Lxym74mWXE'
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
  width: 90%;
  height: auto;
  border-radius: 3px;
}
</style>
