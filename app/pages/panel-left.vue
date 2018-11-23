<template>
  <div class="panel panel-left panel-reveal">
    <f7-navbar :title="name"></f7-navbar>
    <div class="content-block-title">Menu</div>
    <div class="list-block">
      <ul>
        <li>
          <a href="/home/" class="item-link item-content close-panel">
            <div class="item-media"><i class="material-icons">home</i></div>
            <div class="item-inner">
              <div class="item-title">Home</div>
            </div>
          </a>
        </li>
        <li>
          <a href="#" class="item-link item-content close-panel">
            <div class="item-media"><i class="material-icons">face</i></div>
            <div class="item-inner">
              <div class="item-title">Profile</div>
            </div>
          </a>
        </li>
        <li>
          <a href="#" class="item-link item-content close-panel">
            <div class="item-media"><i class="material-icons">settings</i></div>
            <div class="item-inner">
              <div class="item-title">Settings</div>
            </div>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: '',
    }
  },
  created() {
    try {
      this.name = this.$db('userInfo')
    } catch (e) {
      console.log(e)
    }
  },
}
</script>
