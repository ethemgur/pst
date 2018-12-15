<template>
  <div data-page="survey3-video" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/" @click="pause2" ><i class="icon icon-back"></i></a></div>
        <div class="center">STEP 1</div>
      </div>
    </div>
    <a class="floating-button color-purple" @click="navigateURL"><i class="material-icons">navigate_next</i></a>
    <div class="page-content" style="background-color: #f0d2f0">
      <iframe id="yvideo" class="video-content" :src="src" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      src: '',
      q: 0,
      video: '',
      videoElement: null,
      paused: null,
    }
  },
  created() {
    this.getVideo()
    this.src = `https://www.youtube-nocookie.com/embed/${this.video}`
    document.addEventListener('backbutton', this.onBackKeyDown, false)
  },
  methods: {
    pause2() {
      this.src = ''
    },
    onBackKeyDown() {
      this.pause()
      this.$f7.views.main.loadPage('/home/')
    },
    navigateURL() {
      this.pause()
      this.$db(`s3q${this.q}`, null)
      switch ('Evet') {
        case this.$db('s3q1'):
        case this.$db('s3q2'):
        case this.$db('s3q3'):
        case this.$db('s3q4'):
          this.$f7.views.main.refreshPage()
          break
        default:
          this.$f7.views.main.loadPage('/home/')
      }
    },
    getVideo() {
      if (this.$db('s3q1') === 'Evet') {
        this.q = 1
        this.video = 'qw9GEfqUs7A'
      } else if (this.$db('s3q2') === 'Evet') {
        this.q = 2
        this.video = 'zKW9ayKDf-c'
      } else if (this.$db('s3q3') === 'Evet') {
        this.q = 3
        this.video = 'eTVmi3wu2H0'
      } else if (this.$db('s3q4') === 'Evet') {
        this.q = 4
        this.video = 'm_ksoqoGLcQ'
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
  width: 90%;
  height: auto;
  border-radius: 3px;
}
</style>
