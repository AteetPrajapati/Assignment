<template>
  <figure @click="copyURL">
    <img :src="gif.images.original.url" />
    <input
      ref="url"
      readonly
      type="text"
      style="display: none"
      :value="gif.embed_url"
    />
  </figure>
</template>

<script>
export default {
  props: {
    gif: Object,
  },
  methods: {
    copyURL() {
      this.$refs.url.select();
      document.execCommand("copy");
      this.$emit("onSelct", this.gif);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/constants.scss";

figure {
  display: flex;
  flex-direction: column;
  margin: 1rem;
  padding: 0;

  img {
    height: 200px;
  }

  figcaption {
    color: $purple;
    margin: 0.4rem 0;
    overflow-x: auto;

    input {
      color: $primary-font-color;
      margin: 0.3rem 0;
    }
  }
}

button {
  background: transparent;
  border: 1.5px solid $green;
  border-radius: 4px;
  font-weight: bold;
  margin-top: 0.5rem;
  outline: none;
  padding: 0.5rem 1rem;
  text-transform: uppercase;
  transition: all 0.2s;

  &:hover {
    background: $green;
    color: white;
  }
}
</style>