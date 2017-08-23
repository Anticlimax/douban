<template>
  <div class="list" v-scroll="getList">
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
      list: [],
      isLoading: false
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
  directives: {
    scroll: {
      bind(el, binding) {
        window.addEventListener('scroll', () => {
          if (document.body.scrollTop + window.innerHeight >= el.clientHeight) {
            console.log(this)
            let fn = binding.value
            fn()
          }
        })
      }
    }
  },
  mounted() {
    this.getList()
  }
}
</script>

<style lang="scss" scoped>
.list {
  background-image: url('/static/img/background.jpg');
}
</style>
