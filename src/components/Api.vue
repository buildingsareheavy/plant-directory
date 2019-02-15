<template>
  <div id="app">
    <p>Boo!</p>
    <section v-if="errored">
      <p>We're sorry, we're not able to retrieve this information at the moment, please try back later</p>
    </section>

    <section v-else>
      <div v-if="loading">Loading...</div>

      <div v-else v-for="count in data" class="listing">
        <span class="another">
          <!-- {{ Genus }} -->
        </span>
        <span class="other">
          <span v-html="data"></span>
          <!-- {{ Species }} -->
        </span>
      </div>
      <p>Bottom</p>
    </section>
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
      .then(function(res) {
        self.data = res.data;
        console.log("Data:", res.data);
        // this.info = response.data.bpi;
      })
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
