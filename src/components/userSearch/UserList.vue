<template>
  <v-container class="user-list" mt="3">
    <user-card v-for="(user, index) in users" :user="user" :key="index" />
  </v-container>
</template>
<script>
import UserCard from "@/components/userSearch/UserCard.vue";
import users from "@/users";

export default {
  name: "UserList",
  components: {
    UserCard,
  },
  data: function () {
    return {
      users: users.splice(0, 10),
    };
  },
};
</script>
<style scoped lang="scss"></style>
