<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-data-table
          :headers="headers"
          :items="data"
          item-key="name"
          class="elevation-1"
          :search="search"
        >
          <template v-slot:top>
            <v-text-field
              v-model="search"
              label="Search"
              class="mx-4"
            ></v-text-field>
          </template>
        </v-data-table>
      </v-col>
    </v-row>
  </v-container>
</template>


<script>
import dataObj from "../dataObj";
export default {
  data() {
    return {
      search: "",
      data: dataObj,
    };
  },
  computed: {
    headers() {
      return [
        { text: "location", value: "location" },
        { text: "item", value: "item" },
        { text: "brand", value: "brand" },
        { text: "stock", value: "stock" },
      ];
    },
  },
  methods: {},
};
</script>
<style>
</style>