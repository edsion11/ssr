<template>
  <div class="swiperContainer">
    <Swiper ref="mySwiper" :slidesPerView="1" :autoplay="swiperOptions.autoplay" :loop="swiperOptions.loop" :speed="swiperOptions.speed" :pagination="swiperOptions.pagination">
      <swiper-slide v-for="val in data[0].itemMap" :key="val.img" class="sliderContainer" @click="toDetail">
        <img :src="val.img" class="carouselImg">
        <div class="sliderDescContainer">
          <span class="sliderTitle">
            {{ val.title }}
          </span>
        </div>
      </swiper-slide>
      <template #pagination class="swiper-pagination" />
    </Swiper>
  </div>
</template>

<script lang="ts">
import { reactive } from 'vue'
import 'swiper/swiper-bundle.css'
import { Swiper, SwiperSlide } from 'swiper/vue'
import SwiperCore, { Autoplay, Pagination } from 'swiper'
import 'swiper/components/pagination/pagination.less'

SwiperCore.use([Autoplay, Pagination])

export default {
  components: {
    Swiper,
    SwiperSlide
  },
  props: ['data'],
  setup () {
    const swiperOptions = reactive({
      autoplay: {
        delay: 3000,
        disableOnInteraction: false
      },
      loop: true,
      speed: 1000,
      pagination: {
        clickable: true
      }
    })
    return { swiperOptions }
  },

  mounted () {

  },
  methods: {
    toDetail () {
      this.$router.push('/detail/cbba934b14f747049187')
    }
  }
}
</script>

<style lang="less" scoped>
@import "./index.less";
</style>
