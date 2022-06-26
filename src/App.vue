<template>
  <div class="app">
    <MyHeader title="购物车案例" background="pink"/>
    <MyGoods v-for="item in goodList" :key="item.goods_id" :item='item'/>
    <MyFooter :goodList="goodList"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyGoods from './components/MyGoods.vue'
import MyFooter from './components/MyFooter.vue'
import axios from 'axios'
export default {
  data() {
    return {
      goodList: []
    }
  },
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  created () {
    this.getGoods()
  },
  methods: {
    async getGoods() {
      const res = await axios({
        url: '/api/cart'
      })
      this.goodList = res.data.list
      console.log(this.goodList)
    }
  }
}
</script>

<style>
.app {
  padding: 50px 0;
}
</style>
