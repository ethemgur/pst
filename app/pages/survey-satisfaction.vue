<template>
  <div data-page="cards" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a></div>
        <div class="center"> {{title}} </div>
      </div>
    </div>
    <a v-if="current === 0" class="floating-button color-purple" @click="navigateURL"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0; display: flex; align-items: center">
      <div v-if="current !== 0" class="card" style="border-radius: 20px; width:90%; position: absolute; left: 2.5%">
        <div class="card-header"><center>{{q.text}}</center></div>
        <div class="card-content">
          <div class="list-block">
            <ul>
              <span v-for="c in choices">
                <br />
                <li style="margin: 0 10px 0 10px"><a href="#" round="true "class="button button-raised button-fill color-purple" style="border-radius: 50px" @click="select(c)">{{c}}</a></li>
              </span>
              <br />
            </ul>
          </div>
        </div>
      </div>

      <div v-if="current === 0" class="card" style="border-radius: 20px; padding-top: 30px; padding-bottom: 30px; width:90%; position: absolute; left: 2.5%">
        <div style="margin: 10px; text-align: center; font-size: 24px"> {{content}} </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  created() {
    this.current = this.$db('survey')
    this.q = this.questions[this.current]
  },
  methods: {
    navigateURL() {
      if (this.current === 6) {
        this.saveDB()
        this.$db('survey', 0)
        this.$db('satisfaction', 0)
        if (this.$db('currentStep') === 1) {
          this.$f7.views.main.loadPage('/step12/')
        } else {
          this.$f7.views.main.loadPage('/home/')
        }
      } else {
        this.$db('survey', this.current + 1)
        this.$f7.views.main.refreshPage()
      }
    },
    select(c) {
      const score = this.choices.indexOf(c) + 1
      try {
        const total = this.$db('satisfaction')
        this.$db('satisfaction', score + total)
      } catch (e) {
        this.$db('satisfaction', score)
      }
      this.navigateURL()
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
      console.log(this.$db('survey-bdi'))
      console.log(this.$db('currentStep'))
      window.db(`users/${this.$user.uid}/detailed-surveys`)
        .child(this.$db('currentStep')).set({
          bdi: this.$db('bdi'),
          satisfaction: this.$db('satisfaction'),
          selfesteem: this.$db('selfesteem'),
          spsi: this.$db('spsi'),
          stress: this.$db('stress'),
        })
        .then(() => {
          saved = true
          this.$f7.hideIndicator()
        })
        .catch(() => {
          this.$f7.alert('Cannot save new task :-(<br />Please try again later', 'Trouble with Firebase')
          saved = true
          this.$f7.hideIndicator()
        })
    },
  },
  data() {
    return {
      title: 'SATISFACTION SURVEY',
      content: 'Proceed to begin the satisfaction survey.',
      q: {},
      current: 0,
      choices: [
        'I strongly disagree',
        'I do not agree',
        'I disagree slightly.',
        'I agree a little',
        'I agree',
        'Absolutely I agree',
      ],
      questions: [
        {
          id: 0,
          text: '',
        },
        {
          id: 1,
          text: 'My life is close to my ideal in many ways',
        },
        {
          id: 2,
          text: 'My life conditions are perfect',
        },
        {
          id: 3,
          text: 'I am satisfied with my life',
        },
        {
          id: 4,
          text: 'My life is better than most of people',
        },
        {
          id: 5,
          text: 'I got what I wanted from life so far.',
        },
        {
          id: 6,
          text: 'I would not have changed almost anything if I had restarted of my life.',
        },
      ],
    }
  },
}
</script>
