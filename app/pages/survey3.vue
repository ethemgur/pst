<template>
  <div data-page="cards" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a></div>
        <div class="center">GENEL TEST</div>
      </div>
    </div>
    <div class="page-content">
      <div data-pagination=".swiper-pagination" data-pagination-type="progress" data-simulate-touch='false' data-next-button=".survey-next-button" class="swiper-container swiper-init ks-demo-slider">
        <div class="swiper-pagination"></div>
        <div class="swiper-wrapper">

          <!-- STRESS SURVEY -->

          <div class="swiper-slide">
            <div class="page-content">
              <div class="content-block"><center>Şimdi size verilen cümleler üzerinde düşünmenizi ve en uygun olan şıkkı işaretlemenizi isteyeceğiz</center></div>
              <div class="content-block">
                <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">TESTE BAŞLA</a>
              </div>
            </div>
          </div>

          <div class="swiper-slide" v-for="q in questionsList.questions">
            <div class="card">
              <div class="card-header"><center>{{q.text}}</center></div>
              <div class="card-content">
                <div class="list-block">
                  <ul>
                    <span v-for="c in questionsList.choices">
                      <br />
                      <li><a href="#" round="true "class="button button-raised button-fill color-cyan survey-next-button" @click="select(q.id,c)">{{c}}</a></li>
                    </span>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- END OF STRESS SURVEY -->

          <div class="swiper-slide">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">TESTİ BİTİR</a>
          </div>

          <div class="swiper-slide" v-show="$db('s3q1') === 'Evet' ">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">1. video</a>
          </div>

          <div class="swiper-slide" v-show="$db('s3q2') === 'Evet' ">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">2. video</a>
          </div>

          <div class="swiper-slide" v-show="$db('s3q3') === 'Evet' ">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">3. video</a>
          </div>

          <div class="swiper-slide" v-show="$db('s3q4') === 'Evet' ">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">4. video</a>
          </div>

          <div class="swiper-slide" v-show="noProblem">
            <div class="page-content">
              <div class="content-block"><center>Sorunlara yaklaşımınızda bir problem yoktur devam edebilirsiniz</center></div>
              <div class="content-block">
                <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">İLERLE</a>
              </div>
            </div>
          </div>

          <div class="swiper-slide">
            <a href="/home/" class="button button-raised button-fill button-big color-cyan">AŞAMAYI BİTİR</a>
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
          'Evet',
          'Hayır',
        ],
        questions: [
          {
            id: 1,
            text: 'Hayatımdaki zorluk, sıkıntı ve engelleri görmezden gelirim.',
          },
          {
            id: 2,
            text: 'Sorunlar karşısında aklıma ilk geleni uygularım',
          },
          {
            id: 3,
            text: 'Hayatımdaki engelleri aşılamaz, çözülemez olarak görürüm.',
          },
          {
            id: 4,
            text: 'Yaşadığım sıkıntıları faydasız, gereksiz görürüm.',
          },
        ],

      },
    }
  },

  methods: {
    select(q, c) {
      this.$db(`s3q${q}`, c)
      if (c === 'Evet') {
        this.noProblem = false
      }
    },
  },
}
</script>
