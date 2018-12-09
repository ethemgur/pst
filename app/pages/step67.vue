<template>
  <div data-page="video" class="page kitchen-sink-material">
    <a class="floating-button color-cyan" @click="navigateURL"><i class="material-icons">navigate_next</i></a>
    <div class="page-content">
      <h3 style="padding-top:40%">
        Daha önceki çözümlerinizi uygulamak kazançlı olmadığı için bazı aşamaları baştan uygulamanızı istiyoruz.
      </h3>
    </div>
  </div>
</template>
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
