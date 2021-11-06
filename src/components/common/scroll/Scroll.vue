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
    },
    pullUpLoad:{
      type:Boolean,
      default: false
    }
  },
  methods:{
    scrollTo(x, y, time=300) {
      this.scroll.scrollTo(x,y,time)
    },
    finishPullUp() {
      this.scroll.finishPullUp()
    }
  },

  mounted(){
    this.scroll = new BScroll(this.$refs.wrapper, {
      observeDOM: true,
      observeImage: true,
      pullUpLoad: true,
      click: true,
      probeType:this.probeType,
    })

    this.scroll.on('scroll',(position) =>{
      this.$emit('scroll-position',position)
    })

    this.scroll.on('pullingUp',() =>{
      this.$emit('pulling-up')
    })
  },

}
</script>

<style scoped>

</style>