<template>
  <div id="detail">
    <detail-nav-bar></detail-nav-bar>
  </div>
</template>

<script>
  import DetailNavBar from './childComps/DetailNavBar'

  export default {
    name: "Detail",
    components: {
      DetailNavBar,
    },
    data() {
      return {
        iid: null,
        // topImages: [],
        // goods: {},
        // shop: {},
        // detailInfo: {},
        // paramInfo: {}
      }
    },
    created() {
      // 1.保存传入的iid
      console.log(this.$route.params.iid);
      this.iid = this.$route.params.iid

      // 2.根据iid请求详情数据
      // getDetail(this.iid).then(res => {
      //   // 1.获取顶部的图片轮播数据
      //   console.log(res);
      //   const data = res.result;
      //   this.topImages = data.itemInfo.topImages
      //
      //   // 2.获取商品信息
      //   this.goods = new Goods(data.itemInfo, data.columns, data.shopInfo.services)
      //
      //   // 3.创建店铺信息的对象
      //   this.shop = new Shop(data.shopInfo)
      //
      //   // 4.保存商品的详情数据
      //   this.detailInfo = data.detailInfo;
      //
      //   // 5.获取参数的信息
      //   this.paramInfo = new GoodsParam(data.itemParams.info, data.itemParams.rule)
      // })
    },
  }
</script>

<style scoped>

</style>
