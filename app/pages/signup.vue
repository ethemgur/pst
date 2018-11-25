<template>
  <div data-page="sign-up" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">Sign Up</div>
      </div>
    </div>
    <div class="page-content">
      <div class="content-block-title"></div>
      <form class="list-block inputs-list">
        <ul>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">Your name</div>
                <div class="item-input">
                  <input v-model="name" type="text" placeholder="">
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">Gender</div>
                <div class="item-input">
                  <select v-model="gender">
                    <option value=""> </option>
                    <option value="male">Male</option>
                    <option value="female">Female</option>
                  </select>
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title label">Birth date</div>
                <div class="item-input">
                  <input v-model="birthDate" type="date" placeholder="Birth day" value="">
                </div>
              </div>
            </div>
          </li>
        </ul>
        <div class="content-block">
          <p class="buttons-row"><a href="#" class="button button-raised" @click="apply">Apply</a></p>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: '',
      gender: '',
      birthDate: '',
    }
  },

  methods: {
    apply() {
      this.$db('userInfo', {
        name: this.name,
        gender: this.gender,
        birthDate: this.birthDate,
      })
      this.saveDB()
    },

    saveDB() {
      if (!navigator.onLine) {
        window.f7.addNotification({
          title: 'Offline',
          message: 'This action is not possible in offline mode.',
          hold: 3000,
          closeIcon: false,
        })
        return
      }

      // Show loading indicator with delay
      let saved = false
      setTimeout(() => {
        if (!saved) {
          this.$f7.showIndicator()
        }
      }, 1000)
      window.db(`users/${this.$user.uid}`)
        .child('info').set({
          name: this.name,
          gender: this.gender,
          birthDate: this.birthDate,
        })
        .then(() => {
          saved = true
          this.$f7.hideIndicator()
          this.$f7.views.main.loadPage('/home/')
        })
        .catch(() => {
          this.$f7.alert('Cannot save new task :-(<br />Please try again later', 'Trouble with Firebase')
          saved = true
          this.$f7.hideIndicator()
        })
    },
  },
}
</script>
