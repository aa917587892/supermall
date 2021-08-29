<template>
  <swiper ref="swiper" v-if="banners.length">
    <swiper-item v-for="(item,index) in banners">
      <a >
        <img :src="item.image" alt="" @load="imageLoaded">
      </a>
    </swiper-item>
  </swiper>
</template>

<script>
  import {Swiper, SwiperItem} from 'components/common/swiper'

  export default {
    name: "HomeSwiper",
    props: {
      banners: {
        type: Array,
        required: true
      },
       banners2 :[{
              image:'../../assets/img/home/1.jpg'
        },{

        },{
           image:'../../assets/img/home/1.jpg'
        },{
           image:'../../assets/img/home/1.jpg'
        }]

    },
    data() {
    	return {
    		isLoaded: false,

      }
    },
    components: {
      Swiper,
      SwiperItem
    },
    methods: {
      startTimer() {
	      this.$refs.swiper && this.$refs.swiper.startTimer()
      },
      stopTimer() {
        this.$refs.swiper && this.$refs.swiper.stopTimer()
      },
	    imageLoaded() {
        console.log(this.banners);
      	if (!this.isLoaded) {
      		this.$emit('swiperLoaded')
          this.isLoaded = true
        }
	    }
    }
  }
</script>

<style scoped>

</style>