<template>
  <v-app>
    <Toolbar/>
    <v-content>
      <v-container>
        <nuxt/>
      </v-container>
    </v-content>
    <Footer/>
  </v-app>
</template>

<script>
import Toolbar from "~/components/Toolbar.vue";
import Footer from "~/components/Footer.vue";

export default {
  components: {
    Toolbar,
    Footer
  }
};
</script>
