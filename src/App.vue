<template>
  <v-app>
    <v-app-bar app>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://seeklogo.com/images/P/pokeball-logo-DC23868CA1-seeklogo.com.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/1024px-International_Pok%C3%A9mon_logo.svg.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn @click="$vuetify.theme.dark = ! $vuetify.theme.dark" >
        <span class="mr-2">
          Dark Mode
        </span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data() {
    return {};
  },
  methods: {
    cambiarModo() {
      var cuerpoweb = document.body;
      console.log(cuerpoweb);
      cuerpoweb.classList.toggle("oscuro");
    },
  },
};
</script>

<style scoped>
.oscuro {
  background-color: #1f1f1f;
  color: #f1eded;
}
</style>
