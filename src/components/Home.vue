<template>
  <v-card
    class="mx-auto overflow-hidden"
    height="100%"
  >
    <v-app-bar
      color="deep-purple"
      dark
    >
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>

      <v-toolbar-title>D-shop</v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
    >
      <v-list
        nav
        dense
      >
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
    
    <div id ="input-box">
      <Form/>
    </div>
    
    <v-container>
      <hr />
    </v-container>
    
    <div id ="Table">
      <Table/>
    </div>

  </v-card>
</template>

<script>
  import Form from "./Form";
  import Table from "./Table";

  export default {
    components: {
      Form,
      Table
    },
    name: "Home",
    data: () => ({
      drawer: false,
      group: null,
    }),
  }
</script>

<style>

</style>