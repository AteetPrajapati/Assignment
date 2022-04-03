<template #app>
  <div class="postView">
    <gif-search
      @onpost="getmessage"
      class="b-card"
      @fetch-gifs="onFetch"
      @removeSelction="removeSelction"
    />
    <gif-list :gifs="gifs" ref="listofGif" />
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
    };
  },
  methods: {
    getmessage(e) {
      this.posts.push({
        msg: e,
        imgsrc: this.$refs["listofGif"]._data.selectedGiphy,
      });
      console.log(e, this.$refs["listofGif"]._data.selectedGiphy);
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

#app {
  color: $primary-font-color;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;

  ::selection {
    background: $green-light;
  }
}

/* * * * * * */
/* Styled scroll bars */
::-webkit-scrollbar {
  width: 6px;
  height: 6px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey;
  border-radius: 6px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: $green;
  border-radius: 50vh;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: $green-light;
}

/* * * * * * */
</style>
