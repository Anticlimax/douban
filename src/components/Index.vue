<template>
  <div class="index">
    <inner-header class="innerHeader"></inner-header>
    <list class="list"></list>
    <inner-footer class="innerFooter"></inner-footer>
  </div>
</template>

<script>
import innerHeader from './temp/Header.vue'
import innerFooter from './temp/Footer.vue'
import list from './temp/List.vue'

export default {
  components: {
    innerHeader,
    innerFooter,
    list
  }
}
</script>

<style lang="scss" scoped>
.index {
  position: relative;
  height: 100vh;
  >.innerHeader {
    position: fixed;
    top: 0;
    width: 100%;
  }
  >.innerFooter {
    position: fixed;
    bottom: 0;
    width: 100%;
  }
  >.list {
    margin: 70px 0 80px 0; 
  }
}
</style>
