<template>
  <div>
    <div
      style="display: flex; flex-direction: column; height: 500px; width: 500px"
      v-if="selectedGiphy"
    >
      <button @click="remove" style="">Remove</button>
      <img :src="selectedGiphy" />
    </div>
    <section v-else>
      <gif-display
        v-for="gif in gifs"
        :key="gif.id"
        :gif="gif"
        @onSelct="slected"
      />
    </section>
  </div>
</template>

<script>
import GifDisplay from "./GifDisplay";
export default {
  components: { GifDisplay },
  props: {
    gifs: Array,
  },
  data() {
    return {
      selectedGiphy: "",
    };
  },
  methods: {
    remove() {
      this.selectedGiphy = "";
    },
    slected(e) {
      console.log(e);
      this.selectedGiphy = e.images.original.url;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/constants.scss";

section {
  align-items: flex-start;
  border-bottom: $border-purple;
  border-top: $border-purple;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  width: 100%;

  figure {
    width: 40%;
  }
}

@media (min-width: $screen-break-large) {
  section {
    figure {
      width: 20%;
    }
  }
}
</style>