<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div >
      <img alt="pathWith@" src="@/assets/logo.png">
    </div>
    <div >
      <img alt="pathWithRequire" src="require('./assets/logo.png')">
    </div>
    <div class="svgInStyleFromCss"></div>
  </div>
</template>

<script>


export default {
  name: 'app',
  components: {

  }
}
</script>

<style lang="css">

@import "assets/css/a.css";
</style>
