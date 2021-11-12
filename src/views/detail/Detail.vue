<template>
<div id="detail">
  <detail-nav-bar class="detail-nav"/>
  <scroll class="content">
    <div>
      <detail-swiper :top-images="topImages"/>
      <detail-base-info :goods="goods"/>
      <detail-shop-info :shop="shop"/>
      <detail-goods-info :detail-info="detailInfo"/>
    </div>
  </scroll>
</div>
</template>

<script>
import DetailNavBar from "./childComps/DetailNavBar";
import DetailSwiper from "./childComps/DetailSwiper";
import DetailBaseInfo from "./childComps/DetailBaseInfo";
import DetailShopInfo from "./childComps/DetailShopInfo";

import Scroll from "@/components/common/scroll/Scroll";


import {getDetail,Goods,Shop} from "@/network/detail";
import DetailGoodsInfo from "@/views/detail/childComps/DetailGoodsInfo";


export default {
  name: "Detail",
  components:{
    DetailGoodsInfo,
    DetailShopInfo,
    DetailBaseInfo,
    DetailNavBar,
    DetailSwiper,

    Scroll
  },
  data(){
    return{
      iid:null,
      topImages:[],
      goods:{},
      shop:{},
      detailInfo:{}
    }
  },
  created() {
    this.iid = this.$route.params.iid
    getDetail(this.iid).then(res =>{
      console.log(res);
      const data = res.result;
      // 轮播图数据
      this.topImages = data.itemInfo.topImages;
      // 基本信息
      this.goods = new Goods(data.itemInfo,data.columns,data.shopInfo.services)
      // 商铺信息
      this.shop = new Shop(data.shopInfo)
      // 详细信息
      this.detailInfo = data.detailInfo
    })
  }
}
</script>

<style scoped>
#detail{
  position: relative;
  z-index: 9;
  background-color: #f6f6f6;
  height: 100vh;
}

.content{
  height: calc(100% - 44px);
}
</style>