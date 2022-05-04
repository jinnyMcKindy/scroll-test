<template>
  <v-row>
    <v-card
      :loading="loading"
      class="mx-auto my-3"
      width="100%"
      :class="reserved ? 'reserved' : ''"
    >
      <v-row>
        <v-col md="3">
          <v-img
            :key="imgReload"
            height="151.02px"
            class="pa-3 avatar"
            :src="user.avatar"
            @load="loading = false"
          >
            <template v-slot:placeholder>
              <v-row class="ma-0 fill-height" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  height="100%"
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
        </v-col>
        <v-col md="9">
          <div class="grey--text px-3 py-2 float-md-right">
            {{ user.email }}
          </div>
          <v-card-title class="name py-2 px-1">{{ user.name }}</v-card-title>

          <v-card-text class="pb-0 px-1">
            <div class="text-subtitle-1 title">{{ user.title }}</div>
            <div class="text-subtitle-2 city">{{ user.city }}</div>
          </v-card-text>

          <v-card-actions class="px-1">
            <v-btn color="#009688" text @click="reserved = !reserved">
              {{ reserved ? "Skip selection" : "Mark as suitable" }}
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
  data: function () {
    return {
      loading: true,
      imgReload: 0,
      reserved: false,
    };
  },
  methods: {
    /**
     * При ошибке загрузки ставится
     * рандомное время для загрузки каждой картинки,
     * чтобы запросы не шли один за другим
     **/
    onError() {
      setTimeout(() => {
        this.imgReload++;
      }, Math.random(7000, 20000));
    },
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
  min-width: 100px;
}
.title {
  font-family: Roboto;
  font-size: 14px;
  font-weight: 700;
  line-height: 20px;
  color: @grey;
}
.city {
  font-family: Roboto;
  font-size: 14px;
  font-weight: 400;
  line-height: 20px;
  color: @grey;
}
.avatar {
  background-color: @grey;
}
.reserved {
  outline: 1px solid #4765ff;
}
</style>
