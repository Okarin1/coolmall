<template>
<div class="tab-bar-item" @click = "itemClick">
  <div v-if="!isActive"><slot name="item-icon"></slot></div>
  <div v-else><slot name="item-icon-active"></slot></div>
  <div :style="activeStyle"><slot name="item-text"></slot></div>
</div>
</template>

<script>
export default {
  name: "TabBarItem",
  data(){
    return{
    // isActive: true
    }
  },
  props:{
    path:String,
    activeColor:{
      type:String,
      default: '#6799FF'
    }
  },
  methods:{
    itemClick(){
      this.$router.push(this.path).catch(err=>{err})
    }
  },
  computed:{
    isActive(){
      //console.log(this.$route.path.indexOf(this.path))
      return this.$route.path.indexOf(this.path) == 0
    },
    activeStyle(){
      return this.isActive ? {color:this.activeColor} : {}
    }

  }
}
</script>

<style scoped>
.tab-bar-item{
  font-weight: bold;
  flex: 1;
  font-size: 10px ;
  text-align: center;
  height: 49px;
}
.tab-bar-item img{
  width: 28px;
  height: 28px;
  margin-top: 3px;
  vertical-align: middle;
}

</style>
