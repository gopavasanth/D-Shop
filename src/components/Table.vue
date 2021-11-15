<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-data-table
          :headers="headers"
          :items="desserts"
          :items-per-page="5"
          class="elevation-1"
        >
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
      name: "Table",
      headers: [
        {
          text: "Items",
          align: "start",
          sortable: true,
          value: "name",
        },
        { text: "Location", value: "location" },
        { text: "Brand", value: "brand" },
        { text: "Stock", value: "stock" },
      ],
      desserts: dataObj,
    };
  },
};
</script>

<style>
</style>