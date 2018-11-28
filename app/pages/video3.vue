<template>
  <div data-page="video" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a></div>
        <div class="center">Step {{step}}</div>
      </div>
    </div>
    <a :href="'/survey/' + step" class="floating-button color-cyan""><i class="material-icons">navigate_next</i></a>
    <div class="page-content">
      <iframe width="300" src="file:///android_asset/www/cmylmz.mp4"></iframe>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      step: 0,
    }
  },
  created() {
    this.step = this.$route.params.step
  },
}
</script>
