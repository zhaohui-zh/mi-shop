<template>
  <div class="app-init pay-page scroll-box">
    <!-- <header-back title="关于"></header-back> -->

    <div>
      <iframe :src="url" :width="screenWidth" :height="screenHeight"></iframe>
    </div>

  </div>
</template>

<script type="text/ecmascript-6">
  import headerBack from '../../components/header-back'

  export default{
    name: 'live',
    components: {
      headerBack
    },
    data() {
      return {
        url: "https://open.ys7.com/view/h5/6301918a52f94b3281e5bcb8fe2985f8",
        screenWidth: document.body.clientWidth,     // 屏幕宽
        screenHeight: document.body.clientHeight,    // 屏幕高
      }
    }
  }
</script>

<style type="text/sass" lang="sass">
  .pay-page
    background-color: #fff
    .padding-box
      padding: 0.4rem
      color: #333
      .color
        color: orange
      ul
        padding-left: 0.8rem
      li
        list-style: disc
</style>
