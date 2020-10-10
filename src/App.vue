<template>
  <div id="app">
    <v-app>
      <AppBar></AppBar>

      <!-- Sizes your content based upon application components -->
      <v-main>
        <!-- Provides the application the proper gutter -->
        <v-container fluid>
          <!-- If using vue-router -->
          <router-view />
        </v-container>
      </v-main>
      
    </v-app>
  </div>
</template>

<script>
import AppBar from "@/components/AppBar.vue";

export default {
  components: {
    AppBar,
  },
  data() {
    return {};
  },
};
</script>

<style scoped>
.container {
  padding: 30px;
  background-color: #E5E5E5;
}
</style>

