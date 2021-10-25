<template>
  <div>
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners = "banners"/>
<!--    <li v-for="i in banners">{{i.title}}</li>-->
<!--    <li v-for="i in recommends">{{i.title}}</li>-->
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
import HomeSwiper from "./childComps/HomeSwiper";


import {getHomeMultidata} from "@/network/home";


export default {
  name: "Home",
  components:{
    HomeSwiper,
    NavBar,
  },
  data(){
    return{
      banners:[],
      recommends:[]
    }
  },
  created() {
    getHomeMultidata().then(res =>{
      this.banners = res.data.banner.list
      this.recommends = res.data.recommend.list
    })
  }
}
</script>

<style scoped>
.home-nav{
  background-color: var(--color-tint);
  color: white;
  font-size: large;
  font-weight: bold;
}


</style>
