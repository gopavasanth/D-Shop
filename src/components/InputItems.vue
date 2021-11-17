<template>
  <v-select :items="items" label="Items" solo></v-select>
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
console.log(this.location);
export default {
  name: "InputLocation",
  props: {
    location: location,
  },
  methods: {
    // init() {
    //   this.items = this.selectedLocation;
    // },
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