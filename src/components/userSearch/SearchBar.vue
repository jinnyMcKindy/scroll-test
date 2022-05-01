<template>
  <v-card color="grey lighten-4" flat tile>
    <v-toolbar dense>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
      <v-text-field full-width></v-text-field>
    </v-toolbar>
  </v-card>
</template>

<script>
export default {
  name: "SearchBar",
};
</script>
<style scoped>
.theme--light.v-text-field > .v-input__control > .v-input__slot:before {
  border-color: transparent !important;
}
</style>
