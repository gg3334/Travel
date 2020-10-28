<template>
  <ul class="list">
    <li class="item" v-for="(item, key) in cities" :key="key">{{ key }}</li>
  </ul>
</template>

<script>
export default {
  name: "CityAlphabet",
  props: {
    cities: Object,
  },
};
</script>

<style scoped>
.list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: absolute;
  right: 0;
  top: 1.58rem;
  bottom: 0;
  right: 0;
  width: 0.4rem;
}
.item {
  text-align: center;
  line-height: 0.4rem;
  color: #00bcd4;
}
</style>