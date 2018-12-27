<template>
  <div data-page="swiper-horizontal" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner" >
        <div class="left"><a class="back link icon-only" href="#" @click="pause"><i class="icon icon-back"></i></a></div>
        <div class="center">6. AŞAMA</div>
      </div>
    </div>
    <a href="/home/" class="floating-button color-purple" @click="pause"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0">
      <video class="video-content" width="300" controls id="videoElement" @canplay="updatePaused" @playing="updatePaused" @pause="updatePaused" style="border-radius: 20px">
        <source src="file:///android_asset/www/output23.mp4" type="video/mp4" />
      </video>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      videoElement: null,
      paused: null,
    }
  },
  created() {
    document.addEventListener('backbutton', this.onBackKeyDown, false)
  },
  computed: {
    playing() { return !this.paused },
  },
  methods: {
    onBackKeyDown() {
      this.$f7.views.main.loadPage('/home/')
    },
    navigateURL() {
      if (this.saveDB()) {
        this.$f7.views.main.loadPage('/home/')
      }
    },
    saveDB() {
      if (!navigator.onLine) {
        window.f7.addNotification({
          title: 'Offline',
          message: 'İnternet bağlantısı gerekli.',
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
      window.db(`users/${this.$user.uid}`)
        .child('currentStep').set({
          step: 7,
        })
        .then(() => {
          saved = true
          this.$f7.hideIndicator()
        })
        .catch(() => {
          this.$f7.alert('Cannot save new task :-(<br />Please try again later', 'Trouble with Firebase')
          saved = true
          this.$f7.hideIndicator()
          return false
        })
      return true
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
}
</script>
