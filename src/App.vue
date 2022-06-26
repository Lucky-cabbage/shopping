<template>
  <div class="app">
    <MyHeader title="购物车案例" background="hotpink" color="black"></MyHeader>
    <MyGoods></MyGoods>
    <MyFooter></MyFooter>
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
      goodlist: []
    }
  },
  created() {
    this.getgood()
  },
  methods: {
    async getgood() {
      const res = await axios({ url: '/api/cart' })
      // console.log(res)
      this.goodlist = res.data.list
    }
  }
}
</script>

<style>
.app {
  padding: 50px 0;
}
</style>
