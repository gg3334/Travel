<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" />
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "HomeSwiper",
  data() {
    return {
      swiperOption: {
        pagination: ".swiper-pagination",
        loop: true,
      },
      swiperList: [
        {
          id: "0001",
          imgUrl:
            "http://imgs.qunarzz.com/vs_ceph_vcimg/7176acd77332a433af9636eb9a2c338c.jpeg",
        },
        {
          id: "0002",
          imgUrl:
            "http://imgs.qunarzz.com/vs_ceph_vcimg/1cfbdaa2682ada2f854ea6114b3677c8.jpeg",
        },
      ],
    };
  },
};
</script>

<style scoped>
.wrapper >>> .swiper-pagination-bullet-active {
  background: #fff !important;
}
.wrapper {
  overflow: hidden;
  width: 100%;
  height: 0;
  padding-bottom: 31.25%;
  background: #eee;
}
.swiper-img {
  width: 100%;
}
</style>