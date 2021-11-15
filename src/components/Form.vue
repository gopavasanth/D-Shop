<template>
  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col cols="12" md="4">
          <v-select :items="locations" label="Location" solo></v-select>
        </v-col>

        <v-col cols="12" md="4">
          <v-select :items="items" label="Items" solo></v-select>
        </v-col>

        <v-col cols="12" md="4">
          <v-select :items="brands" label="Brand" solo></v-select>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="6" md="4" class="text-right">
          <v-btn depressed color="primary"> Apply Filters </v-btn>
        </v-col>
        <v-col cols="6" md="4" class="text-right">
          <v-btn depressed color="error"> Reset </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
import dataObj from "../dataObj";

const locations = [];
const items = [];
const brands = [];
for (var i = 0; i < dataObj.length; i++) {
  var obj = dataObj[i];
  locations.push(obj.location);
  items.push(obj.name);
  brands.push(obj.brand);
}

export default {
  name: "Form",
  data: () => ({
    search: "",
    valid: false,
    locations: locations,
    items: items,
    brands: brands,
  }),
};
</script>

<style>
</style>