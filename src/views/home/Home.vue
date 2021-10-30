<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommends" />
    <feature-view/>
    <tab-control  class="tab-control" :titles="['流行', '新款', '精选']"></tab-control>
    <ul>
      <li>商品1</li>
      <li>商品2</li>
      <li>商品3</li>
      <li>商品4</li>
      <li>商品5</li>
      <li>商品6</li>
      <li>商品7</li>
      <li>商品8</li>
      <li>商品9</li>
      <li>商品10</li>
      <li>商品11</li>
      <li>商品12</li>
      <li>商品13</li>
      <li>商品14</li>
      <li>商品15</li>
      <li>商品16</li>
      <li>商品17</li>
      <li>商品18</li>
      <li>商品19</li>
      <li>商品20</li>
      <li>商品21</li>
      <li>商品22</li>
      <li>商品23</li>
      <li>商品24</li>
      <li>商品25</li>
      <li>商品26</li>
      <li>商品27</li>
      <li>商品28</li>
      <li>商品29</li>
      <li>商品30</li>
      <li>商品31</li>
      <li>商品32</li>
      <li>商品33</li>
      <li>商品34</li>
      <li>商品35</li>
      <li>商品36</li>
      <li>商品37</li>
      <li>商品38</li>
      <li>商品39</li>
      <li>商品40</li>
      <li>商品41</li>
      <li>商品42</li>
      <li>商品43</li>
      <li>商品44</li>
      <li>商品45</li>
      <li>商品46</li>
      <li>商品47</li>
      <li>商品48</li>
      <li>商品49</li>
      <li>商品50</li>
      <li>商品51</li>
      <li>商品52</li>
      <li>商品53</li>
      <li>商品54</li>
      <li>商品55</li>
      <li>商品56</li>
      <li>商品57</li>
      <li>商品58</li>
      <li>商品59</li>
      <li>商品60</li>
      <li>商品61</li>
      <li>商品62</li>
      <li>商品63</li>
      <li>商品64</li>
      <li>商品65</li>
      <li>商品66</li>
      <li>商品67</li>
      <li>商品68</li>
      <li>商品69</li>
      <li>商品70</li>
      <li>商品71</li>
      <li>商品72</li>
      <li>商品73</li>
      <li>商品74</li>
      <li>商品75</li>
      <li>商品76</li>
      <li>商品77</li>
      <li>商品78</li>
      <li>商品79</li>
      <li>商品80</li>
      <li>商品81</li>
      <li>商品82</li>
      <li>商品83</li>
      <li>商品84</li>
      <li>商品85</li>
      <li>商品86</li>
      <li>商品87</li>
      <li>商品88</li>
      <li>商品89</li>
      <li>商品90</li>
      <li>商品91</li>
      <li>商品92</li>
      <li>商品93</li>
      <li>商品94</li>
      <li>商品95</li>
      <li>商品96</li>
      <li>商品97</li>
      <li>商品98</li>
      <li>商品99</li>
      <li>商品100</li>
    </ul>


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

import {getHomeMultidata} from "@/network/home";



export default {
  name: "Home",
  components:{
    RecommendView,
    HomeSwiper,
    FeatureView,

    NavBar,
    TabControl

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
#home{
  padding-top: 44px;
}
.home-nav{
  background-color: var(--color-tint);
  color: white;
  font-size: large;
  font-weight: bold;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
}
.tab-control{
  position:sticky;
  top:44px
}


</style>
