<template>
  <div data-page="cards" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a></div>
        <div class="center">GENEL TEST</div>
      </div>
    </div>
    <div class="page-content">

      <div class="card" style="padding-top: 50%">
        <div class="card-header"><center>Planladığınız aşamaları hayata geçirdiniz mi?</center></div>
        <div class="card-content">
          <div class="list-block">
            <ul>
              <br />
              <li><a href="#" round="true "class="button button-raised button-fill color-cyan" @click="select(true)">Evet</a></li>
              <br />
              <li><a href="#" round="true "class="button button-raised button-fill color-cyan" @click="select(false)">Hayır</a></li>
            </ul>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>
<script>
export default {
  methods: {
    select(c) {
      if (c === true) {
        console.log('Evet')
      } else {
        console.log('Hayır')
      }
      this.$f7.views.main.loadPage('/step82/')
    },
  },
}
</script>
