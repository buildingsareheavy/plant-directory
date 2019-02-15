<template>
  <div id="app">{{ info }}</div>
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
  filters: {
    currencydecimal(value) {
      return value.toFixed(2);
    }
  },

  mounted() {
    this.axios
      .request({
        url: "/kingdoms",
        method: "get",
        baseURL: "https://trefle.io/api",
        headers: {
          Authorization: "Bearer YVhSTmJqVWZZN2NJczZ0d3NKMHpMZz09"
        }
      })
      .then(response => {
        this.info = response.data.bpi;
      })
      .catch(error => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  }
};
</script>

<style></style>
