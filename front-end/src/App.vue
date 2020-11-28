<template>
<v-app id="inspire">
  <v-icon>fas fa-list</v-icon>
    <!-- <v-system-bar app>
      <v-spacer></v-spacer>
<v-icon>fas fa-list</v-icon>
    </v-system-bar> -->
      <!-- <v-btn v- @click="Navigation" text rounded>Navigation</v-btn> -->
      <v-btn @click="toggleTheme" text rounded>toggle Theme</v-btn>
    <navigation />
    
    
    <v-main>
      <v-container
        class="py-8 px-6"
        fluid
      >
      <router-view></router-view>
        <v-row>
          11
          <v-icon>fas fa-list</v-icon>
          <v-col
            v-for="card in cards"
            :key="card"
            cols="12"
          >
            <v-card>
              <v-subheader>{{ card }}</v-subheader>

              <v-list two-line>
                <template v-for="n in 6">
                  <v-list-item

                    :key="n"
                  >
                    <v-list-item-avatar color="grey darken-1">
                    </v-list-item-avatar>

                    <v-list-item-content>
                      <v-list-item-title>Message {{ n }}</v-list-item-title>

                      <v-list-item-subtitle>
                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nihil repellendus distinctio similique
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
import Navigation from '@/components/common/Navigation.vue'


export default {
  name: 'App',

  components: {
    Navigation
  },

  data: () => ({
     cards: ['Today', 'Yesterday'],
      // drawer: null,
      // links: [
      //   ['mdi-inbox-arrow-down', 'Home'],
      //   ['mdi-send', 'About'],
      //   ['mdi-delete', 'Trash'],
      //   ['mdi-alert-octagon', 'Spam'],
      // ],
  }),
  methods:{

    toggleTheme(){
      this.$vuetify.theme.dark=!this.$vuetify.theme.dark
    }
  }
};
</script>
