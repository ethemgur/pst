<template>
  <div data-page="cards" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a></div>
        <div class="center">GENERAL TEST</div>
      </div>
    </div>
    <div class="page-content">
      <div data-pagination=".swiper-pagination" data-pagination-type="progress" data-simulate-touch='false' data-allow-touch-move='false' data-next-button=".survey-next-button" class="swiper-container swiper-init ks-demo-slider">
        <div class="swiper-pagination"></div>
        <div class="swiper-wrapper">

          <!-- SURVEY -->

          <div class="swiper-slide" style="background-color: #f0d2f0; display: flex; align-items: center">
            <div class="card" style="border-radius:20px; padding-top: 10px; padding-bottom:10px">
              <div class="card-header">
                <div style="text-align: center; font-size: 18px"> Now we will ask you to think about the sentences given to you and mark the most appropriate</div>
              </div>
              <div class="card-content" style="padding: 10px">
                <a href="#" class="button button-raised button-fill button-big color-purple survey-next-button" style="border-radius:20px">START TO TEST</a>
              </div>
            </div>
          </div>

          <div class="swiper-slide" v-for="q in questionsList.questions" style="background-color: #f0d2f0" >
            <div class="card" style="border-radius:20px">
              <div class="card-header"><center>{{q.text}}</center></div>
              <div class="card-content">
                <div class="list-block">
                  <ul>
                    <span v-for="c in questionsList.choices">
                      <li  style="margin: 10px; padding: 5px"><a href="#" round="true "class="button button-raised button-fill color-purple survey-next-button" @click="select(q.id,c)" style="border-radius: 20px"">{{c}}</a></li>
                    </span>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- END OF SURVEY -->



          <div class="swiper-slide" style="background-color: #f0d2f0">
            <a class="floating-button color-purple" @click="navigateURL"><i class="material-icons">navigate_next</i></a>
            <div class="card" style="border-radius: 20px; position:absolute; top: 40%">
              <div class="card-header" style="text-align: center; font-size:20px"> FINISH THE TEST </div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>
<script>
module.exports = {
  data() {
    return {
      noProblem: true,
      questionsList: {

        choices: [
          'Yes',
          'No',
        ],
        questions: [
          {
            id: 1,
            text: 'I ignore the difficulties, distress and obstacles in my life.',
          },
          {
            id: 2,
            text: 'I apply my first thought to the problems',
          },
          {
            id: 3,
            text: 'I see the obstacles in my life as insurmountable.',
          },
          {
            id: 4,
            text: 'I see the problems I have experienced are useless, unnecessary.',
          },
        ],

      },
    }
  },
  created() {
    document.addEventListener('backbutton', this.onBackKeyDown, false)
  },
  methods: {
    onBackKeyDown() {
      this.pause()
      this.$f7.views.main.loadPage('/home/')
    },
    select(q, c) {
      this.$db(`s3q${q}`, c)
      if (c === 'Yes') {
        this.noProblem = false
      }
      console.log(this.noProblem)
    },
    navigateURL() {
      this.$db('currentStep', 2)
      for (let i = 1; i < 5; i++) {
        if (this.$db(`s3q${i}`) === 'Yes') {
          this.noProblem = false
        }
      }
      if (this.noProblem) {
        this.$f7.views.main.loadPage('/home/')
      } else {
        this.$db('s3-noProblem', false)
        this.$f7.views.main.loadPage('/survey3-video/')
      }
    },
  },
}
</script>

<style media="screen">
.video-content
{
  position: absolute;
  margin: auto;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  width: 95%;
  border-radius: 3px;
}
</style>
</script>
