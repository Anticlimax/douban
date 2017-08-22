<template>
  <div class="listItem">
    <div class="itemWrapper" :style="`background-image:url(${data.images.large})`">
      <!-- <div class="title">{{data.title}}</div> -->
    </div>
  </div>
</template>

<script>
export default {
  props: ['data']
}
</script>

<style lang="scss" scoped>
  .listItem {
    height: 450px;
    .itemWrapper {
      height: 100%;

      background-size: cover;
      background-repeat: no-repeat;
      background-position: center center;
    }
  }
</style>
