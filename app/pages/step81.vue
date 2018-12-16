<template>
  <div data-page="cards" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="link icon-only" href="/home/"><i class="icon icon-back"></i></a></div>
        <div class="center">STEP 7</div>
      </div>
    </div>
    <div class="page-content" style="background-color: #f0d2f0; display: flex; align-items: center">
      <div class="card" style="border-radius: 20px; width:100%;">
        <div class="card-header">
          <div style="text-align:center; width: 100%; padding: 5px">Did you accomplish the stages you planned?</div>
        </div>
        <div class="card-content">
          <div class="list-block" style="padding: 20px 10px">
            <ul>
              <li><a href="#" round="true "class="button button-raised button-fill color-purple" style="border-radius: 20px; margin:0 10px 0 10px" @click="select(true)">Yes</a></li>
            </br>
            <li><a href="#" round="true "class="button button-raised button-fill color-purple" style="border-radius: 20px; margin:0 10px 0 10px" @click="select(false)">No</a></li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</div>
</template>
<script>
export default {
  created() {
    document.addEventListener('backbutton', this.onBackKeyDown, false)
  },
  methods: {
    onBackKeyDown() {
      this.$f7.views.main.loadPage('/home/')
    },
    select(c) {
      if (c === true) {
        console.log('Yes')
        this.$db('step81-ans', 'No')
      } else {
        console.log('Hayır')
        this.$db('step81-ans', 'No')
      }
      this.$f7.views.main.loadPage('/step82/')
    },
  },
}
</script>
