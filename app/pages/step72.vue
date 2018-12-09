<template>
  <div data-page="step72" class="page kitchen-sink-material">
    <a class="floating-button color-cyan" @click="navigateURL"><i class="material-icons">navigate_next</i></a>
    <div class="page-content">
      <h3 style="padding-top: 40%">
        Şimdi bu aşamaları uygulayın
      </h3>
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
