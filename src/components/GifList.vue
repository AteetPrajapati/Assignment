<template>
  <div class="row">
    <div class="col">
      <figure class="figure" v-if="selectedGiphy">
        <img class="figure-img img-fluid rounded" :src="selectedGiphy" />
        <figcaption class="figure-caption">
          <button
            type="button"
            class="btn btn-primary"
            @click="remove"
            style=""
          >
            Remove
          </button>
        </figcaption>
      </figure>
      <div class="row" v-else>
        <gif-display
          v-for="gif in gifs"
          :key="gif.id"
          :gif="gif"
          @onSelct="slected"
        />
      </div>
    </div>
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
</style>