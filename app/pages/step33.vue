<template>
  <div data-page="video" class="page kitchen-sink-material">
    <a href="/home/" class="floating-button color-cyan" @click="save"><i class="material-icons">navigate_next</i></a>
    <div class="page-content">
      <h3 style="padding-top:30%">
        <center>
          Şimdi bu hedefin gerçekleşmesi için neler yapılabileceğini düşünün.
        </center>
      </h3>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    save() {
      this.$db('step3', true)
    },
  },
}
</script>
