<template>
  <div data-page="swiper-horizontal" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/" @click="pause2" ><i class="icon icon-back"></i></a></div>
        <div class="center">{{title}}</div>
      </div>
    </div>
    <a :href="'step311' " class="floating-button color-purple" @click="pause2"><i class="material-icons">navigate_next</i></a>

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
      title: 'STEP 3',
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
    pause2() {
      this.src = ''
    },
    onBackKeyDown() {
      this.pause()
      this.$f7.views.main.loadPage('/home/')
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
}
</style>
