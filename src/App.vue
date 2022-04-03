<template #app>
  <div class="container" style="padding-top: 50px">
    <gif-search
      v-if="render"
      @onpost="getmessage"
      @fetch-gifs="onFetch"
      @removeSelction="removeSelction"
    />
    <gif-list v-if="render" :gifs="gifs" ref="listofGif" />
    <postList :images="posts" />
  </div>
</template>

<script>
import GifList from "./components/GifList";
import GifSearch from "./components/GifSearch";
import postList from "./components/postList.vue";

export default {
  watch: {},
  name: "App",
  components: { GifList, GifSearch, postList },
  data() {
    return {
      gifs: [],
      posts: [],
      render: true,
    };
  },
  methods: {
    getmessage(e) {
      this.posts.push({
        msg: e,
        imgsrc: this.$refs["listofGif"]._data.selectedGiphy,
      });
      console.log(e, this.$refs["listofGif"]._data.selectedGiphy);
      this.removeSelction();
      this.render = false;
      this.gifs = [];
      setTimeout(() => {
        this.render = true;
      }, 500);
    },
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
@import "./assets/constants.scss";
</style>
