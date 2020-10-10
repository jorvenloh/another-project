<template>
  <div>
    <SideBar :drawer="drawer"></SideBar>
    <v-app-bar app flat color="primary">
      <v-app-bar-nav-icon
        class="hidden-xl-and-up"
        @click="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <div class="v-toolbar__title">Dashboard</div>

      <div class="spacer"></div>

      <div>
        <div class="d-inline-block">
          <v-text-field
            label="Search"            
            hide-details="auto"  
            append-icon="mdi-search"      
            background-color="primary darken-1" 
            rounded  
          ></v-text-field>          
        </div>
        <v-divider color="secondary" inset vertical></v-divider>
        <div class="d-inline mx-3">Jorven Loh</div>
        <v-avatar color="secondary" size="36">
          <span class="white--text">JL</span>
        </v-avatar>
      </div>
    </v-app-bar>
  </div>
</template>

<script>
import SideBar from "@/components/SideBar.vue";

export default {
  components: { SideBar },
  data() {
    return {
      drawer: true,
    };
  },
};
</script>

<style>
</style>