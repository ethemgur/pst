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
        <div class="card-header"><center>Bu çözümü uygulamak kazançlı mı?</center></div>
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
        this.$f7.views.main.loadPage('/step71/')
      } else {
        const el = JSON.parse(localStorage.getItem('solutions'))
        el.splice(0, 1)
        localStorage.setItem('solutions', JSON.stringify(el))
        if (el.length > 0) {
          this.$f7.views.main.loadPage('/step66/')
        } else {
          this.$f7.views.main.loadPage('/step67/')
        }
      }
    },
  },
}
</script>
