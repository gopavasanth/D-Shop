<template>
  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col cols="12" md="4">
          <v-select
            :items="locations"
            label="Location"
            v-model="selectedLocation"
            solo
            @change="onChangeLocation"
          ></v-select>
        </v-col>

        <v-col cols="12" md="2">
          <v-select
            :items="items"
            label="Items"
            v-model="selectedItem"
            @change="onChangeItem"
            solo
          ></v-select>
        </v-col>

        <v-col cols="12" md="2">
          <v-select
            :items="brands"
            label="Brand"
            v-model="selectedBrand"
            solo
          ></v-select>
        </v-col>
        <v-col cols="12" md="2">
          <v-btn depressed color="primary" @click="applyFilters">
            Apply Filters
          </v-btn>
        </v-col>
        <v-col cols="12" md="2">
          <v-btn depressed color="error" @click="resetFilters"> Reset </v-btn>
        </v-col>
      </v-row>

      <v-row>
        <v-col>
          <v-btn depressed color="secondary" outlined small @click="viewCart">
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
  name: "Home",
  methods: {
    onChangeLocation() {
      this.items = [];
      for (let i = 0; i < datanew[this.selectedLocation].length; i++) {
        this.items.push(datanew[this.selectedLocation][i].item);
      }
    },
    onChangeItem() {
      this.brands = [];
      for (let i = 0; i < datanew[this.selectedLocation].length; i++) {
        this.brands.push(datanew[this.selectedLocation][i].brand);
      }
    },
    applyFilters() {
      this.data = this.data.filter((data) => {
        return (
          (data.location == this.selectedLocation ||
            this.selectedLocation == "") &&
          (data.item == this.selectedItem || this.selectedItem == "") &&
          (data.brand == this.selectedBrand || this.selectedBrand == "")
        );
      });
    },
    resetFilters() {
      (this.locations = locations),
        (this.items = ""),
        (this.brands = ""),
        (this.data = tableData),
        (this.selected = []);
    },
    viewCart() {
      Object.values(this.selected).map((it) => {
        this.selectedRows.push([it.id, it.item, it.location, it.brand]);
      });
      alert(this.selectedRows);
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
    selectedLocation: "",
    selectedItem: "",
    selectedBrand: "",
    locations: locations,
    items: [],
    brands: [],
  }),
  watch: {
    selected: function () {
      Object.values(this.selected).map((it) => {
        console.log(it.item);
      });
    },
  },
};
</script>

<style>
</style>