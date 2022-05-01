<template>
  <v-text-field outlined full-width :value="search" @input="fetchDebounced">
    <template v-slot:label>
      <v-icon style="vertical-align: left">mdi-magnify</v-icon>
    </template>
  </v-text-field>
</template>

<script>
export default {
  name: "SearchBar",
  data: function () {
    return {
      search: "",
    };
  },
  watch: {
    "$route.query.search": {
      handler: function (matchString) {
        if (!matchString || this.search === matchString) {
          return;
        }
        this.search = matchString;
      },
      deep: true,
      immediate: true,
    },
  },
  methods: {
    fetchDebounced(val) {
      clearTimeout(this._timerId);
      this._timerId = setTimeout(() => {
        this.setQuery(val);
      }, 500);
    },
    setQuery(val) {
      this.$router.push({ name: "Home", query: { search: val } });
    },
  },
};
</script>
<style>
.v-text-field__details {
  display: none !important;
}
</style>
