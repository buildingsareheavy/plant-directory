<template>
  <div id="app">
    <h1>PLANTS!</h1>
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
      .get("https://trefle.io/api", {
        params: {
          key: "YVhSTmJqVWZZN2NJczZ0d3NKMHpMZz09"
        }
      })
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
