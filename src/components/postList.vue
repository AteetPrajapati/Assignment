<template #app>
  <div class="row">
    <div
      v-for="(e, i) in images"
      :key="i"
      class="col-5 card m-3 center w-100 mx-auto"
      aria-current="true"
    >
      <div class="w-100">
        <h5 class="mb-1 text-center">{{ e.msg }}</h5>
        <img
          :src="e.imgsrc"
          class="rounded mx-auto d-block my-2"
          style="height: 400px; width: 400px"
        />
      </div>
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
