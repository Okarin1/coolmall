<template>
  <div>
    <swiper class="detail-swiper">
      <swiper-item class="item" v-for="item in topImages" >
        <img :src="item" alt="">
      </swiper-item>
    </swiper>
  </div>
</template>

<script>
  import {Swiper, SwiperItem} from 'components/common/swiper'

	export default {
		name: "DetailSwiper",
    components: {
		  Swiper,
      SwiperItem
    },
    props: {
		  topImages: {
		    type: Array,
        default() {
		      return []
        }
      }
    }
	}
</script>

<style scoped>
  .item {
    text-align: center;
    height: 300px;
  }
</style>
