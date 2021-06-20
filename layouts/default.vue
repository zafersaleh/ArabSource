<template>
  <v-app>
    <Nav />

    <v-main class="pa-0">
      <nuxt />
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Nav from "@/components/Nav.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Footer,
    Nav
  }
};
</script>

<style lang="scss" scoped></style>
