<template>
  <div class="col-3" @click="copyURL">
    <img :src="gif.images.original.url" class="img-thumbnail" alt="..." />
    <input
      ref="url"
      readonly
      type="text"
      style="display: none"
      :value="gif.embed_url"
    />
  </div>
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
</style>