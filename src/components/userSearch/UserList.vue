<template>
  <v-container class="user-list">
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
      total: [...users],
      users: [],
      index: 0,
      hash: {},
      matchString: "",
      step: 20,
    };
  },
  created() {
    window.addEventListener("scroll", this.scrollFunc);
    this.users = [...users].splice(0, this.step);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.scrollFunc);
  },
  watch: {
    "$route.query.search": {
      handler: function (matchString) {
        this.matchString = matchString;
        if (!matchString) {
          this.users = [...this.total].splice(0, this.step);
          this.index = 0;
          return;
        }
        if (this.hash[matchString]) {
          this.users = [...this.hash[matchString].splice(0, this.step)];
        } else {
          this.search(matchString);
        }
      },
      deep: true,
      immediate: true,
    },
  },
  methods: {
    debounce(method, delay) {
      clearTimeout(method._tId);
      method._tId = setTimeout(function () {
        method();
      }, delay);
    },
    scrollFunc() {
      this.debounce(this.handleScroll, 100);
    },
    handleScroll() {
      if (
        Math.ceil(window.innerHeight * 2) + Math.ceil(window.scrollY) >=
        document.body.offsetHeight - Math.ceil(window.scrollY)
      ) {
        const target = this.matchString
          ? this.hash[this.matchString]
          : this.total;
        if (target.length === this.users.length) return;
        this.index += this.step;
        const newUsers = [...target].splice(this.index, this.step);
        this.users = [...this.users, ...newUsers];
      }
    },
    search(matchString) {
      function compare(value) {
        return value.toLowerCase().indexOf(matchString.toLowerCase()) > -1;
      }
      const found = this.total.filter((user) => {
        return (
          compare(user.name) ||
          compare(user.city) ||
          compare(user.title) ||
          compare(user.email)
        );
      });
      this.hash[matchString] = [...found];
      this.users = found.splice(0, this.step);
    },
  },
};
</script>
<style scoped lang="scss"></style>
