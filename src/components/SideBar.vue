<template>
  <v-navigation-drawer app v-model="drawer" dark color="secondary">
    <template v-slot:prepend>
      <v-avatar color="primary ma-5" size="56">
        <span class="white--text">LOGO</span>
      </v-avatar>
    </template>

    <v-list nav>
      <v-list-item
        v-for="item in navigations"
        :key="item.title"
        :to="item.route"
      >
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list-item
        v-for="setting in settings"
        :key="setting.title"
        :to="setting.route"
      >
        <v-list-item-icon>
          <v-icon>{{ setting.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ setting.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  props: {
    drawer: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      navigations: [
        { title: "Overview", icon: "pie_chart", route: "/" },
        { title: "Tickets", icon: "local_activity", route: "/tickets" },
        { title: "Ideas", icon: "emoji_objects", route: "/ideas" },
        {
          title: "Contacts",
          icon: "mdi-account-group-outline",
          route: "/contacts",
        },
        { title: "Agents", icon: "mdi-account", route: "/agents" },
        { title: "Articles", icon: "description", route: "/articles" },
      ],
      settings: [
        { title: "Setting", icon: "settings", route: "/setting" },
        { title: "Subscription", icon: "card_membership", route: "/subscriptions" },
      ],
    };
  },
};
</script>

<style>
</style>