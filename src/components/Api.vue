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
          "Access-Control-Allow-Origin": "*",
          "Access-Control-Allow-Methods":
            "GET, POST, PATCH, PUT, DELETE, OPTIONS",
          "Access-Control-Allow-Headers": "Origin, Content-Type, X-Auth-Token",
          Authorization: "Bearer" + "YVhSTmJqVWZZN2NJczZ0d3NKMHpMZz09"
        }
      })
      .then(response => {
        this.info = response.data.bpi;
      })
      .catch(error => {
        // eslint-disable-next-line
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  }
};
</script>

<style></style>
