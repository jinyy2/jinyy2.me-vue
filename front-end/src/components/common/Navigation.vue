<template>
  <v-navigation-drawer v-model="drawer" app>
    <v-sheet color="grey lighten-4" class="pa-4">
      <v-avatar class="mb-4" color="grey darken-1" size="64"></v-avatar>

      <div>jy5031le@gmail.com</div>
    </v-sheet>

    <v-divider></v-divider>

    <v-list>
      <v-list-item v-for="[icon, text] in links" :key="icon" link>
        <v-list-item-icon>
          <v-icon>{{ icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title @click="move(text)">{{ text }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
<script>
export default {
  name: "Navigation",
    data: () => ({
      drawer: null,
      links: [
        ["mdi-inbox-arrow-down", "Home"],
        ["mdi-send", "About"],
        ["mdi-delete", "Trash"],
        ["mdi-alert-octagon", "Spam"],
      ],
    }),
  methods: {
    move(m) {
      // alert(m)
      this.$router.push(`${m}`);
    },
  },
  watch: {
      drawer: () => {
        // alert(x)
      },
    },
};
</script>
<style scoped>
</style>