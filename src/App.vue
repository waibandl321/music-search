<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <router-link to="/">
        <span class="mr-2" style="color: #fff;">Music Search</span>
        </router-link>
      
      </div>

      <v-spacer></v-spacer>

      <v-btn
        to="/"
        text
      >
        <span class="mr-2">Home</span>
      </v-btn>
    </v-app-bar>

    <v-main>
     <router-view/>
    </v-main>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  // components: {
  //   HelloWorld,
  // },

  data: () => ({
    //
  }),
};
</script>
