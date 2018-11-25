<template>
  <div data-page="list-view" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a href="#" class="open-panel"><i class="material-icons" style="color: white; margin: 50%">menu</i></a></div>
        <div class="center" style="margin: 10%">Profile</div>
      </div>
    </div>
    <div class="page-content" :style="{'background-image': 'url(' + require('../images/green-bg.jpg') + ')'}" style="background-size: cover">
      <div class="card ks-facebook-card" style="background-color: rgba(0,0,0,0.15)">
        <div class="card-content" style="padding-top: 30%">
          <center><h3>{{userInfo.name}}</h3></center>
          <div class="card-content-inner">
            <p class="color-black">Days: 112</p>
          </div>
        </div>
        <div class="card-footer">
          <a class=""></a>
          <a href="#" class="link button color-orange" @click="edit = true" v-show="!edit">EDIT</a>
          <a href="#" class="link button color-orange" @click="editHandler" v-show="edit">DONE</a>
        </div>
      </div>

      <div class="content-block-title"></div>
      <form class="list-block inputs-list" v-if="!edit">
        <ul>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">{{userInfo.name}}</div>
                <div class="item-input">
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">{{userInfo.gender}}</div>
                <div class="item-input">
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">{{userInfo.birthDate}}</div>
                <div class="item-input">
                </div>
              </div>
            </div>
          </li>
        </ul>
      </form>
      <form class="list-block inputs-list" v-if="edit">
        <ul v-if="edit">
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
                    <option value="male" v-if="userInfo.gender === 'male'">Male</option>
                    <option value="female">Female</option>
                    <option value="male" v-if="userInfo.gender === 'female'">Male</option>
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
                  <input v-model="birthDate" type="date" placeholder="Birth day">
                </div>
              </div>
            </div>
          </li>
        </ul>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      userInfo: {},
      name: '',
      gender: '',
      birthDate: '',
      edit: false,
      editText: 'EDIT',
    }
  },
  created() {
    try {
      this.userInfo = this.$db('userInfo')
    } catch (e) {
      console.log(e)
    }
    this.birthDate = userInfo.birthDate
  },
  methods: {
    validation() {
      if (this.name == '') {
        this.name = this.userInfo.name
      }
      if (this.gender == '') {
        this.gender = this.userInfo.gender
      }
      if (this.birthDate == '') {
        this.birthDate = this.userInfo.birthDate
      }
    },
    editHandler() {
      this.validation()
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
          this.$f7.views.main.refreshPage()
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
