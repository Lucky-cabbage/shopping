<template>
  <div class="app">
    <MyHeader title="购物车案例" background="hotpink" color="black"></MyHeader>
    <MyGoods
      v-for="item in goodslist"
      :key="item.goods_id"
      :goods="item"
    ></MyGoods>
    <MyFooter :goodslist="goodslist"></MyFooter>
  </div>
</template>

<script>
import MyHeader from '@/components/MyHeader.vue'
import MyGoods from '@/components/MyGoods.vue'
import MyFooter from '@/components/MyFooter.vue'
import axios from 'axios'
export default {
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  data() {
    return {
      goodslist: []
    }
  },
  created() {
    this.getgoods()
  },
  methods: {
    async getgoods() {
      const res = await axios({ url: '/api/cart' })
      // console.log(res)
      this.goodslist = res.data.list
    }
  }
}
</script>

<style>
.app {
  overflow: auto;
  max-height: 100vh;
  box-sizing: border-box;
  padding: 50px 0;
}
</style>
