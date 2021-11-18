<template>
  <v-card class="mx-auto overflow-hidden" height="100%">
    <v-app-bar color="deep-black" dark>
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>

      <v-toolbar-title>D-shop</v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" absolute temporary>
      <v-list nav dense>
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item>

          <!-- <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account</v-icon>
            </v-list-item-icon>
            <v-list-item-title>App1</v-list-item-title>
          </v-list-item> -->
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <div id="input-box">
      <Home />
    </div>
  </v-card>
</template>

<script>
import Home from "./Home";

export default {
  components: {
    Home,
  },
  name: "Index",
  data: () => ({
    drawer: false,
    group: null,
  }),
};
</script>

<style>
</style>