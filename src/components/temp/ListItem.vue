<template>
  <div class="listItem">
    <div class="itemWrapper">
      <img :src="data.images.large">
      <div class="infoWrapper">
        <div class="infoItem">{{data.title}}({{data.year}})</div>
        <div class="infoItem">主演：{{actor}}</div>
        <div class="infoItem">导演：{{data.directors[0].name}}</div>
        <div class="infoItem">类型：{{type}}</div>
        <div class="infoItem">评分：{{data.rating.average}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['data'],
  computed: {
    type() {
      const movieType = this.data.genres.join('、')
      return movieType
    },
    actor() {
      let arr = []
      this.data.casts.forEach(i => {
        arr.push(i.name)
      })
      return arr.join('、')
    }
  }
}
</script>

<style lang="scss" scoped>
  .listItem {
    height: 450px;
    .itemWrapper {
      box-sizing: border-box;
      height: 100%;
      padding: 30px;
      display: flex;

      img {
        height: 100%;
        object-fit: cover;
        border-radius: 5px;
      }
      .infoWrapper {
        font-size: 30px;
        color: white;
        .infoItem {
          margin: 20px
        }
      }
    }
  }
</style>
