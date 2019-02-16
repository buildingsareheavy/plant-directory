<template>
  <div id="app">
    <h1>PLANTS!</h1>
    <div v-for="(data, key) in info.data">
      <div class="data">{{ data.Genus }}</div>
      <div class="span">
        <span v-html="data"></span>
      </div>
      <div class="info">{{ data.Species }}</div>
      <br>
      <br>
    </div>
  </div>
</template>

<script>
export default {
  name: "API",
  data() {
    return {
      info: null,
      loading: true,
      errored: false
    };
  },
  mounted() {
    let self = this;
    this.axios
      .get("https://plantsdb.xyz/search?limit=10&fields=Genus,Species")
      .then(response => (this.info = response.data))
      .catch(error => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  }
};
</script>

<style>
.listing {
  border: 1px solid black;
}
.another {
  background: green;
}

.other {
  background: yellow;
}
</style>
