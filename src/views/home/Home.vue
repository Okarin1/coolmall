<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <tab-control  class="tab-control"
                  :titles="['流行', '新款', '精选']"
                  @tabClick="tabClick"
                  ref="tabControl1"
                  v-show="isTabFixed"/>
    <scroll class="content" ref="scroll"
            :probe-type="3"
            @scroll-position="contentScroll"
            :pull-up-load="true"
            @pulling-up="loadMore">
      <div>
        <home-swiper :banners="banners"
                     @swiper-image-load="swiperImageLoad"/>
        <recommend-view :recommends="recommends" />
        <feature-view/>
        <tab-control  class="tab-control"
                      :titles="['流行', '新款', '精选']"
                      @tabClick="tabClick"
                      ref="tabControl2"/>
        <goods-list :goods="showGoods"/>
      </div>
    </scroll>
    <back-top @click.native="backClick" v-show="isShowBackTop"/>



  </div>
</template>

<script>

// 子组件
import HomeSwiper from "./childComps/HomeSwiper";
import RecommendView from "./childComps/RecommendView";
import FeatureView from "@/views/home/childComps/FeatureView";


// 公共组件
import NavBar from "@/components/common/navbar/NavBar";
import TabControl from "@/components/content/tabControl/TabControl";
import GoodsList from "@/components/content/goods/GoodsList";
import Scroll from "@/components/common/scroll/Scroll";
import BackTop from "@/components/content/backTop/BackTop";

import {getHomeMultidata,getHomeGoods} from "@/network/home";



export default {
  name: "Home",
  components:{
    RecommendView,
    HomeSwiper,
    FeatureView,
    Scroll,

    NavBar,
    TabControl,
    GoodsList,
    BackTop

  },
  data(){
    return{
      banners:[],
      recommends:[],
      goods:{
        'pop':{page:0,list:[]},
        'new':{page:0,list:[]},
        'sell':{page:0,list:[]},
      },
      currertType:['pop','new','sell'],
      currertIndex:0,
      isShowBackTop: false,
      topOffsetTop:0,
      isTabFixed:false
    }
  },
  created() {
    this.getHomeMultidata(),
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')
  },
  computed:{
    showGoods(){
      return this.goods[this.currertType[this.currertIndex]].list
    }
  },

  methods: {
    getHomeMultidata() {
      getHomeMultidata().then(res => {
        this.banners = res.data.banner.list
        // console.log(res)
        this.recommends = res.data.recommend.list
      })
    },

    getHomeGoods(type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type,page).then(res =>{
        this.goods[type].list.push(...res.data.list)
        this.goods[type].page += 1
        this.$refs.scroll.finishPullUp()
      })
    },

    tabClick(index){
      this.currertIndex = index
      this.$refs.tabControl1.currertIndex = index
      this.$refs.tabControl2.currertIndex = index
    },

    backClick() {
      this.$refs.scroll.scrollTo(0,0,500)
    },
    contentScroll(position){
      this.isShowBackTop =  (-position.y) > 1000
      this.isTabFixed = (-position.y)>this.topOffsetTop
      },
    loadMore() {
      this.getHomeGoods(this.currertType[this.currertIndex])
    },
    swiperImageLoad(){
      this.topOffsetTop = this.$refs.tabControl2.$el.offsetTop;
    }


  }


}
</script>

<style scoped>
#home{
  /*padding-top: 44px;*/
  height: 100vh;
  position: relative;
}
.home-nav{
  background-color: var(--color-tint);
  color: white;
  font-size: large;
  font-weight: bold;
  /*position: fixed;*/
  /*left: 0;*/
  /*right: 0;*/
  /*top: 0;*/
  /*z-index: 9;*/
}
.tab-control{
  position:sticky;
  top:44px;
  z-index:9;
}


.content {
  overflow: hidden;
  position: absolute;
  top: 44px;
  bottom: 49px;

}
/*.fixed{*/
/*  position: fixed;*/
/*  left: 0;*/
/*  right: 0;*/
/*  top: 44px;*/
/*}*/

</style>
