<template>
    <div class="guide_wrap">
      <swiper :options="swiperOption" ref="mySwiper" v-if="guide">
        <swiper-slide><img src="../assets/36_img.png" alt=""></swiper-slide>
        <swiper-slide><img src="../assets/37_img.png" alt=""></swiper-slide>
        <swiper-slide><img src="../assets/38_img.png" alt="" @click="startUse"></swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
      <div class="guide_page" v-else>
        <img src="../assets/54_img.png" alt="">
        <h1>蓝穹</h1>
      </div>
    </div>
</template>

<script>
import "swiper/dist/css/swiper.css";
import { swiper, swiperSlide } from "vue-awesome-swiper";
export default {
  data() {
    var self = this;
    return {
      swiperOption: {
        autoplay: false,
        notNextTick: true,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          paginationClickable: false,
          paginationType: "custom"
        },
        on: {
          sliderMove: function() {
            if (this.activeIndex + 1 == 3) {
              self.startUse();
            }
          }
        }
      },
      guide: true
    };
  },
  components: {
    swiper,
    swiperSlide
  },
  computed: {
    swiper() {
      return this.$refs.mySwiper.swiper;
    }
  },
  methods: {
    startUse() {
      var self = this;
      self.guide = false;
      setTimeout(function() {
        self.$router.push("home");
      }, 750);
    }
  }
};
</script>