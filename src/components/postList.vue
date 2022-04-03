<template #app>
  <div class="postView">
    <div v-for="(e, i) in images" :key="i">
      <p>{{ e.msg }}</p>
      <img :src="e.imgsrc" />
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  props: ["images"],
  data() {
    return {
      gifs: [],
      posts: [],
    };
  },
  methods: {
    removeSelction() {
      console.log(this.$refs["listofGif"]._data.selectedGiphy);
      this.$refs["listofGif"]._data.selectedGiphy = "";
    },
    onFetch(result) {
      this.gifs = result;
    },
  },
};
</script>

<style lang="scss">
// @import "./assets/constants.scss";
</style>
