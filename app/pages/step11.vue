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
            <p><center>Şimdi sizden bazı testleri cevaplamanızı isteyeceğiz. Testlere başlamak için ilerleyin</center></p>
          </div>

          <div class="swiper-slide">
            <a :href="/survey2/" class="floating-button color-cyan" @click="validationAlert"><i class="material-icons">navigate_next</i></a>
            <center>Testlere başlamak için ilerleyin</center>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>
<script>

</script>
