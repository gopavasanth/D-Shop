<template>
  <v-card class="mx-auto overflow-hidden" height="100%">
    <v-app-bar color="deep-black" dark>
      <v-toolbar-title>{{ title }}</v-toolbar-title>
    </v-app-bar>
  </v-card>
</template>

<script>
export default {
  name: "Header",
  props: ["title"],
  data: () => ({
    drawer: false,
    group: null,
  }),
};
</script>

<style>
</style>