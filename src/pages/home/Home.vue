<template>
  <div>
    <home-header />
    <home-swiper :list="swiperList" />
    <home-icons :list="iconList" />
    <home-recommend :list="recommendList" />
    <home-weekend :list="weekendList" />
  </div>
</template>

<script>
import HomeHeader from "./components/Header";
import HomeSwiper from "./components/Swiper";
import HomeIcons from "./components/Icons";
import HomeRecommend from "./components/Recommend";
import HomeWeekend from "./components/Weekend";
import axios from "axios";
import { mapState } from "vuex";

export default {
  name: "Home",
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend,
  },
  data() {
    return {
      lastCity: "",
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: [],
    };
  },
  computed: {
    ...mapState(["city"]),
  },
  methods: {
    getHoemInfo() {
      axios.get("/api/index.json?city=" + this.city).then(this.getHoemInfoSucc);
    },
    getHoemInfoSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        this.swiperList = res.data.swiperList;
        this.iconList = res.data.iconList;
        this.recommendList = res.data.recommendList;
        this.weekendList = res.data.weekendList;
      }
      console.log(res);
    },
  },
  mounted() {
    this.lastCity = this.city;
    this.getHoemInfo();
  },
  activated() {
    if (this.lastCity != this.city) {
      this.lastCity = this.city;
      this.getHoemInfo();
    }
  },
};
</script>

<style scoped>
</style>