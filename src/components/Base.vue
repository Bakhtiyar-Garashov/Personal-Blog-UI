<template >
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-email</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Contact</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="green" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Blog</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-text-field
        style="max-width:40%;float:right"
        :append-icon-cb="() => {}"
        placeholder="Search..."
        single-line
        append-icon="mdi-magnify"
        color="white"
        hide-details
      ></v-text-field>
    </v-app-bar>
    <v-main>
      <v-container class="fill-height grey lighten-5" fluid>
        <v-row>
          <Posts />
        </v-row>
      </v-container>
    </v-main>
    <v-footer padless>
      <v-card flat tile width="100%" class="green text-center">
        <v-card-text>
          <v-btn v-for="icon in icons" :key="icon" class="mx-4" icon>
            <v-icon size="24px">{{ icon }}</v-icon>
          </v-btn>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} —
          <small>powered by &nbsp;</small>
          <strong>Bakhtiyar</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
import Posts from "../components/Posts";

export default {
  components: {
    Posts,
  },
  data: () => ({
    drawer: false,
    icons: [
      "mdi-facebook",
      "mdi-instagram",
      "mdi-twitter",
      "mdi-email",
      "mdi-github",
    ],
  }),
};
</script>
