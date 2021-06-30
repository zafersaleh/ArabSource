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

<style lang="scss">
.page-enter-active,
.page-leave-active {
  transition: opacity 0.25s ease-in-out, transform 0.25s ease-in-out;
}
.page-enter,
.page-leave-to {
  opacity: 0;
  transform: translate3d(0, 15px, 0);
}
</style>
