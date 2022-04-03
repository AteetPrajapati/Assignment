<template>
  <form>
    <div class="row">
      <div class="col">
        <div class="input-group mb-3">
          <input
            v-model="value0fmsg"
            type="text"
            placeholder="Type Here your Message"
            class="form-control"
            aria-label="Recipient's username"
            aria-describedby="button-addon2"
          />
        </div>
        <div class="input-group mb-3">
          <input
            placeholder="What gifs do you want to look at?"
            v-model="keyword"
            @input="onInput"
            class="form-control"
            float="right"
          />
        </div>
        <div class="input-group mb-3">
          <button
            class="btn btn-outline-secondary"
            type="button"
            id="button-addon2"
            @click="postthePost"
          >
            POST
          </button>
        </div>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      keyword: "",
      timeout: null,
      value0fmsg: "",
    };
  },
  methods: {
    postthePost(e) {
      e.preventDefault();
      this.$emit("onpost", this.value0fmsg);
      this.keyword = "";
    },
    remove(e) {
      e.preventDefault();
      this.$emit("removeSelction", "");
    },
    onInput() {
      clearTimeout(this.timeout);
      this.timeout = setTimeout(() => {
        this.search();
      }, 500);
    },
    search() {
      console.log("API Key is: " + process.env.VUE_APP_GIPHY_API_KEY);
      fetch(
        `https://api.giphy.com/v1/gifs/search?api_key=${process.env.VUE_APP_GIPHY_API_KEY}&q=${this.keyword}&limit=12`
      )
        .then((response) => response.json())
        .then((res) => {
          console.log(res);
          this.$emit("fetch-gifs", res.data);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/constants.scss";
</style>