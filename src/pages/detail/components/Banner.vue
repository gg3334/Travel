<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="info.bannerImg" alt="" />
      <div class="banner-info">
        <div class="banner-title">{{ info.sightName }}</div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe8ba;</span
          >{{ info.gallaryImgs.length }}
        </div>
      </div>
    </div>
    <common-gallary
      :imgs="imgs"
      v-show="showGallary"
      @close="handleGallaryClose"
    ></common-gallary>
  </div>
</template>

<script>
import CommonGallary from "common/gallary/Gallary";

export default {
  name: "DetailBanner",
  props: {
    info: Object,
  },
  data() {
    return {
      showGallary: false,
      // imgs: this.info.gallaryImgs,
    };
  },
  computed: {
    imgs() {
      return this.info.gallaryImgs;
    },
  },
  components: {
    CommonGallary,
  },
  methods: {
    handleBannerClick() {
      this.showGallary = true;
    },
    handleGallaryClose() {
      this.showGallary = false;
    },
  },
};
</script>

<style scoped>
.banner {
  position: relative;
  overflow: hidden;
  height: 0;
  padding-bottom: 55%;
  color: #fff;
}
.banner-img {
  width: 100%;
}
.banner-info {
  display: flex;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  line-height: 0.6rem;
  background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));
}
.banner-title {
  flex: 1;
  font-size: 0.14rem;
  padding: 0 0.2rem;
}
.banner-number {
  margin-top: 0.2rem;
  padding: 0 0.4rem;
  height: 0.32rem;
  line-height: 0.32rem;
  border-radius: 0.2rem;
  background: rgba(0, 0, 0, 0.8);
  font-size: 0.24rem;
}
.banner-icon {
  font-size: 0.24rem;
}
</style>