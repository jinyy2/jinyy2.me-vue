<template>
  <v-app id="inspire">
    <!-- <v-btn @click="toggleTheme" text rounded>toggle Theme</v-btn> -->

    <!-- <navigation /> -->
    <v-navigation-drawer v-model="drawer" app>
      <v-sheet color="grey lighten-1" class="pa-4">
        <v-avatar class="mb-4" color="grey darken-1" size="64"></v-avatar>

        <div>jy5031le@gmail.com</div>
      </v-sheet>

      <v-divider></v-divider>

      <v-list>
        <v-switch
          class="pl-8"
          v-model="$vuetify.theme.dark"
          inset
          color="indigo darken-3"
          label="Dark Mode"
          persistent-hint
        ></v-switch>
        <v-list-item v-for="[icon, text] in links" :key="icon" link>
          <v-list-item-icon>
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title @click="move(text)">{{
              text
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-btn v-if="!drawer" @click="drawer = true">nav-bar</v-btn>
      <v-container class="py-8 px-6" fluid>
        <router-view></router-view>
        <v-row>
          <v-icon>fas fa-list</v-icon>
          <v-col v-for="card in cards" :key="card" cols="12">
            <v-card>
              <v-subheader>{{ card }}</v-subheader>

              <v-list two-line>
                <template v-for="n in 6">
                  <v-list-item :key="n">
                    <v-list-item-avatar color="grey darken-1">
                    </v-list-item-avatar>

                    <v-list-item-content>
                      <v-list-item-title>Message {{ n }}</v-list-item-title>

                      <v-list-item-subtitle>
                        Lorem ipsum dolor sit amet, consectetur adipisicing
                        elit. Nihil repellendus distinctio similique
                      </v-list-item-subtitle>
                    </v-list-item-content>
                  </v-list-item>

                  <v-divider
                    v-if="n !== 6"
                    :key="`divider-${n}`"
                    inset
                  ></v-divider>
                </template>
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
  <!-- <v-app>
    <v-btn @click="toggleTheme" text rounded>toggle Theme</v-btn>
    <v-main>
    <router-view />
    </v-main>
  </v-app> -->
</template>

<script>
// import Navigation from "@/components/common/Navigation.vue";

export default {
  name: "App",

  components: {
    // Navigation,
  },

  data: () => ({
    cards: ["Today", "Yesterday"],
    drawer: null,
    theme: false,
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
    toggleTheme() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    },
  },
  watch: {
    theme() {
      this.toggleTheme();
    },
  },
};
</script>
