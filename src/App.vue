<template>
  <v-app height="100vh">
    <!-- <v-card > -->
    <v-navigation-drawer app fixed permanent left>
      <template v-slot:prepend>
        <v-list-item two-line>
          <v-list-item-avatar>
            <img src="https://picsum.photos/seed/picsum/200/300">
          </v-list-item-avatar>

          <v-list-item-content style="margin: 10px;">
            <v-list-item-title>Ирина</v-list-item-title>
            <v-list-item-subtitle>test@email.com</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>

      <v-divider></v-divider>

      <v-list dense>

        <v-list-item link :to="'/'" style="font-weight: 700;">
          <!-- <v-icon>{{ this.icons.mdiShareVariant }}</v-icon> -->
          <img src="./assets/home.svg" width="24px" style="margin: 10px;" />
          <v-list-item-content>
            <v-list-item-title>Все новости</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item link :to="'/create'" style="font-weight: 700;">
          <!-- <v-icon>{{ icons.mdiShareVariant }}</v-icon> -->

          <img src="./assets/create.svg" width="24px" style="margin: 10px;" />
          <v-list-item-content>
            <v-list-item-title>Добавить запись</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

      </v-list>
    </v-navigation-drawer>
    <!-- </v-card> -->
    <v-main>

      <!-- Provides the application the proper gutter -->
      <v-container>

        <!-- If using vue-router -->
        <router-view></router-view>
      </v-container>
    </v-main>
  </v-app>

</template>

<script>
import create from "./assets/create.svg";
import home from "./assets/home.svg"
export default {

  name: 'App',
  data() {
    return {
      icons: {
        create,
        home,
        mdiShareVariant,
        mdiDelete,
      },
    }
  },
};
</script>
<style>
.v-list-item--dense .v-list-item__title,
.v-list-item--dense .v-list-item__subtitle,
.v-list--dense .v-list-item .v-list-item__title,
.v-list--dense .v-list-item .v-list-item__subtitle {
  font-weight: 700 !important;
}

.v-list-item--link:before {
  background: none !important;

}

.v-list .v-list-item--active {
  color: rgb(9, 180, 248) !important;
}

nav.v-navigation-drawer.v-navigation-drawer--fixed.v-navigation-drawer--open.theme--light {
  box-shadow: rgba(14, 30, 37, 0.12) 0px 2px 4px 0px, rgba(14, 30, 37, 0.32) 0px 2px 16px 0px !important;

}

.v-main__wrap {
  background-color: #aaaaaa40;
}
</style>