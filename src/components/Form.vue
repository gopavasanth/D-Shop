<template>
  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col cols="12" md="4">
          <v-select
            :items="locations"
            label="Location"
            v-model="location"
            solo
            @change="onChangeLocation"
          ></v-select>
        </v-col>

        <v-col cols="12" md="4">
          <v-select
            :items="items"
            label="Items"
            v-model="item"
            @change="onChangeItem"
            solo
          ></v-select>
        </v-col>

        <v-col cols="12" md="4">
          <v-select
            :items="brands"
            label="Brand"
            v-model="brand"
            solo
          ></v-select>
        </v-col>
      </v-row>

      <v-row>
        <v-col class="my-0 py-0 mt-1">
          <v-btn depressed color="primary" @click="applyFilters">
            Apply Filters
          </v-btn>
        </v-col>
        <v-col class="ma-0 pa-0 mt-1">
          <v-btn depressed color="error" @click="resetFilters"> Reset </v-btn>
        </v-col>
        <v-col class="ma-0 pa-0 mt-1">
          <v-btn depressed color="secondary" @click="viewCart">
            View Cart
          </v-btn>
        </v-col>

        <v-col class="text-right">
          <download-excel :data="data" type="csv" name="DshopCatalogue.csv">
            <v-btn color="success" outlined small
              ><v-icon size="20">mdi-file-excel</v-icon>Download</v-btn
            >
          </download-excel>
        </v-col>
      </v-row>
      <v-container>
        <hr />
      </v-container>
      <v-row>
        <v-col cols="12">
          <v-data-table
            :headers="headers"
            :items="data"
            class="elevation-1"
            :search="search"
            item-key="id"
            v-model="selected"
            :single-select="singleSelect"
            show-select
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
  </v-form>
</template>

<script>
import tableData from "../dataObj";
import datanew from "../dataObjsNew";

const locations = [...Object.keys(datanew)];

export default {
  name: "Form",
  methods: {
    onChangeLocation() {
      this.items = [];
      for (let i = 0; i < datanew[this.location].length; i++) {
        this.items.push(datanew[this.location][i].item);
      }
    },
    onChangeItem() {
      this.brands = [];
      for (let i = 0; i < datanew[this.location].length; i++) {
        this.brands.push(datanew[this.location][i].brand);
      }
    },
    applyFilters() {
      this.data = this.data.filter((data) => {
        return (
          (data.location == this.location || this.location == "") &&
          (data.item == this.item || this.item == "") &&
          (data.brand == this.brand || this.brand == "")
        );
      });
    },
    resetFilters() {
      (this.locations = locations), (this.items = ""), (this.brands = "");
    },
    viewCart() {
      Object.values(this.selected).map((it) => {
        this.selectedRows.push([it.item, it.location, it.brand]);
      });
      alert(this.selectedRows + "\n");
      this.selected = "";
    },
  },
  computed: {},
  data: () => ({
    headers: [
      { text: "ID", value: "id" },
      { text: "Location", value: "location" },
      { text: "Item", value: "item" },
      { text: "Brand", value: "brand" },
      { text: "Stock", value: "stock" },
    ],
    singleSelect: false,
    selected: [],
    selectedRows: [],
    data: tableData,
    search: "",
    valid: false,
    location: "",
    item: "",
    brand: "",
    locations: locations,
    items: [],
    brands: [],
  }),
  watch: {
    selected: function () {
      console.log(this.selected);
      // Object.values(this.selected).map((item) => {
      //   // console.log(item.id);
      // });
    },
  },
};
</script>

<style>
</style>