<template>
  <div class="footer">
    <div class="footerItem" v-for="item in footerItem" @click="linkTo(item)" :class="{active: item.active}">
      {{item.text}}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      footerItem: [
        {
          text: '首页',
          router: '',
          active: true
        },
        {
          text: '收藏',
          router: '',
          active: false
        }
      ]
    }
  },
  methods: {
    linkTo(item) {
      this.footerItem.forEach(i => {
        i.active = false
      })
      item.active = true
    }
  }
}
</script>

<style lang="scss" scoped>
.footer {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 80px;


  font-size: 30px;
  background-color: #f7f7f7;
  opacity: .9;
  .footerItem {
    flex-grow: 1;

    text-align: center;
    border-right: 1px solid lightgray;
    color: #939aa0;
    &:last-child {
      border: none;
    }
  }
  .active {
    color: black;
  }
}
</style>
