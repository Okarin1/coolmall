<template>
  <div class="wrapper" ref="wrapper">
      <slot></slot>
  </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name: "Scroll",
  data(){
    return{
      scroll:null
    }
  },
  props:{
    probeType:{
      type:Number,
      default:0
    }
  },
  methods:{
    scrollTo(x, y, time=300) {
      this.scroll.scrollTo(x,y,time)
    }
  },

  mounted(){
    this.scroll = new BScroll(this.$refs.wrapper, {
      observeDOM: true,
      observeImage: true,
      click: true,
      probeType:this.probeType,
    })

    this.scroll.on('scroll',(position) =>{
      this.$emit('scroll-position',position)
    })
  },

}
</script>

<style scoped>

</style>