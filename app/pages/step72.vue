<template>
  <div data-page="swiper-horizontal" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner" >
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">7. ADIM</div>
      </div>
    </div>
    <a href="/step81/" class="floating-button color-purple"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0; display: flex; align-items: center">
      <div class="card" style="border-radius: 20px; padding-top: 30px; padding-bottom: 30px">
        <div style="margin: 10px; text-align: center; font-size: 24px">Şimdi bu aşamaları uygulayın </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    navigateURL() {
      if (this.saveDB()) {
        this.$f7.views.main.loadPage('/step81/')
      }
    },
    saveDB() {
      if (!navigator.onLine) {
        window.f7.addNotification({
          title: 'Offline',
          message: 'This action is not possible in offline mode.',
          hold: 3000,
          closeIcon: false,
        })
        return false
      }
      let saved = false
      setTimeout(() => {
        if (!saved) {
          this.$f7.showIndicator()
        }
      }, 1000)
      const plans = JSON.parse(localStorage.getItem('plans'))
      // eslint-disable-next-line no-restricted-syntax
      for (const p in plans) {
        // Show loading indicator with delay
        const el = plans[p]
        window.db(`users/${this.$user.uid}`)
          .child(el.text).set({
            text: el.text,
          })
          .then(() => {
            saved = true
            this.$f7.hideIndicator()
          })
          .catch(() => {
          // this.$f7.alert('Cannot save new task :-(<br />Please try again later', 'Trouble with Firebase')
            saved = true
            this.$f7.hideIndicator()
            return false
          })
      }
      return true
    },
  },
}
</script>
