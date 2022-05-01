<template>
  <v-row>
    <v-card :loading="loading" class="mx-auto my-3" width="100%">
      <template slot="progress">
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        ></v-progress-linear>
      </template>
      <v-row>
        <v-col md="3">
          <v-img height="auto" class="pa-3 avatar" :src="user.avatar"></v-img>
        </v-col>
        <v-col md="9">
          <div class="grey--text px-3 float-md-right">{{ user.email }}</div>
          <v-card-title class="name py-2 px-1">{{ user.name }}</v-card-title>

          <v-card-text class="pb-0 px-1">
            <div class="text-subtitle-1 title">{{ user.title }}</div>
            <div class="text-subtitle-2 city">{{ user.city }}</div>
          </v-card-text>

          <v-card-actions class="px-1">
            <v-btn color="#009688" text @click="reserve">
              Mark as suitable
            </v-btn>
          </v-card-actions>
        </v-col>
      </v-row>
    </v-card>
  </v-row>
</template>

<script>
export default {
  name: "UserCard",
  props: {
    user: Object,
  },
};
</script>

<style scoped lang="less">
@grey: #0000008b;
.name {
  font-family: Roboto;
  font-size: 24px;
  font-weight: 400;
  line-height: 32px;
  letter-spacing: 0em;
  text-align: left;
  min-width: 100px;
}
.title {
  font-family: Roboto;
  font-size: 14px;
  font-weight: 700;
  line-height: 20px;
  letter-spacing: 0em;
  text-align: left;
  color: @grey;
}
.city {
  font-family: Roboto;
  font-size: 14px;
  font-weight: 400;
  line-height: 20px;
  letter-spacing: 0em;
  text-align: left;
  color: @grey;
}
.avatar {
  background-color: @grey;
}
</style>
