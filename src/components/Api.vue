<template>
  <div id="app">
    <h1>PLANTS!</h1>
    <div v-for="(data) in info.data">
      <div class="data data-all">
        <div class="data">
          <span class="name-science">Scientific Name:</span>
          {{ data.Genus }} {{ data.Species }}
        </div>
        <div class="data" v-if="data.Common_Name">
          <span class="name-common">Common Name:</span>
          {{ data.Common_Name }}
        </div>
        <div class="data" v-else>
          <span class="name-common-none">Common name doesn't exist</span>
        </div>
      </div>
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
    this.axios
      .get("https://plantsdb.xyz/search?limit=10")
      .then(response => (this.info = response.data))
      .catch(error => {
        // console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  }
};
</script>

<style scoped lang="scss">
.data-all {
  margin: 2rem auto;
  display: inline-block;
  background: black;
}

.data {
  padding: 0.5rem;
  color: white;
  span {
    padding: 0.25rem 0.5rem;
    color: black;
  }
}
.name-science {
  background: skyblue;
}
.name-common {
  background: lightgreen;
}
.name-common-none {
  background: tomato;
}
</style>
