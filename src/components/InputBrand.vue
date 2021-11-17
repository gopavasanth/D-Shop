<template>
  <v-select :items="brands" label="Brand" solo></v-select>
</template>

<script>
import dataObj from "../dataObj";
import datanew from "../dataObjsNew";

console.log(datanew);
const locations = [...Object.keys(datanew)];

const items = [];
const brands = [];

for (var i = 0; i < dataObj.length; i++) {
  var obj = dataObj[i];
  items.push(obj.name);
  brands.push(obj.brand);
}

export default {
  name: "InputLocation",
  props: {
    selected: {
      // type: String,
    },
  },
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