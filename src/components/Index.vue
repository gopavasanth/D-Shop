<template>
  <v-card class="mx-auto overflow-hidden" height="100%">
    <div id="header">
      <Header :title="title" />
    </div>

    <div id="home">
      <Home />
    </div>
  </v-card>
</template>

<script>
import Home from "./Home";
import Header from "./Header";

export default {
  components: {
    Home,
    Header,
  },
  name: "Index",
  data: () => ({
    drawer: false,
    group: null,
    title: "D-Shop - Inventory Application",
  }),
};
</script>

<style>
</style>