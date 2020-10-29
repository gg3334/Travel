<template>
  <div>
    <detail-banner :info="detailInfo"></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="detailList"></detail-list>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import DetailBanner from "./components/Banner";
import DetailHeader from "./components/Header";
import DetailList from "./components/List";

export default {
  name: "Detail",
  data() {
    return {
      detailList: [],
      detailInfo: {},
    };
  },
  components: {
    DetailBanner,
    DetailHeader,
    DetailList,
  },
  methods: {
    getDetailInfo() {
      axios.get("api/detail.json").then((res) => {
        this.detailList = res.data.data.categoryList;
        this.detailInfo = res.data.data;
      });
    },
  },
  mounted() {
    this.getDetailInfo();
  },
};
</script>

<style scoped>
.content {
  height: 50rem;
}
</style>