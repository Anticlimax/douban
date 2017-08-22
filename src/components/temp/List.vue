<template>
  <div class="list">
    <list-item v-for="item in this.list" :data="item" :key="item.id"></list-item>
  </div>
</template>

<script>
import axios from 'axios'
import listItem from './ListItem.vue'

export default {
  components: {
    listItem
  },
  data() {
    return {
      start: 0,
      count: 10,
      list: []
    }
  },
  methods: {
    getList() {
      const { start, count } = this
      axios.get('/v2/movie/top250', { params: { start, count } }).then(res => {
        if (res.status === 200) {
          this.list.push(...res.data.subjects)
          this.start += 10
        }
      })
    }
  },
  mounted() {
    this.getList()
  }
}
</script>

<style lang="scss" scoped>

</style>
