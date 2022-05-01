<template>
  <v-container class="wrapper">
    <search-bar />
    <user-list />
  </v-container>
</template>

<script>
import UserList from "@/components/userSearch/UserList.vue";
import SearchBar from "@/components/userSearch/SearchBar.vue";
export default {
  name: "UserSearch",
  components: {
    UserList,
    SearchBar,
  },
};
</script>
<style scoped lang="scss">
.wrapper {
  width: 700px !important;
  max-width: 100%;
}
</style>
