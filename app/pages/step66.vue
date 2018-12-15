<template>
  <div data-page="step66" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#" @click="pause2"><i class="icon icon-back"></i></a></div>
        <div class="center">STEP 6</div>
      </div>
    </div>
    <a :href="'/step61/' + step" class="floating-button color-purple" @click="pause2"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0">
      <div class= content>
        <div class="card" style="border-radius: 20px">
          <iframe id="yvideo" class="video-content" :src="src" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
      </div>

    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      src: '',
    }
  },
  created() {
    this.src = 'https://www.youtube.com/embed/B_-oYh4SM64'
    document.addEventListener('backbutton', this.onBackKeyDown, false)
  },
  methods: {
    pause2() {
      this.src = ''
    },
    onBackKeyDown() {
      this.$f7.views.main.loadPage('/home/')
    },
  },
}
</script>
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
