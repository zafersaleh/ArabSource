<template>
  <v-parallax id="hii" height="750" src="hi1.png">
    <v-row align="center" justify="center" class="ma-0">
      <v-col class="text-center" lg="6" md="10" cols="12">
        <v-img
          class="mb-5"
          style="margin:auto"
          max-height="100px"
          max-width="150px"
          src="logo2.png"
          eager
        ></v-img>
        <h4 class="subheading text-justify">
          {{ arabicinfo.header.description }}
        </h4>
      </v-col>
    </v-row>
    <!-- <v-img height="750px" width="100%" src="caver.png"></v-img> -->
    <!-- <lottie-player
      src="https://assets5.lottiefiles.com/packages/lf20_vubims6l.json"
      background="transparent"
      speed="1"
      style="width: 300px; height: 300px;"
      loop
      autoplay
    ></lottie-player> -->
    <!-- <lottie-player
      src="https://assets9.lottiefiles.com/packages/lf20_zIOoIe.json"
      background="transparent"
      speed="1"
      style="width: 300px; height: 200px;position: absolute;
    bottom: 0; left:10px"
      loop
      autoplay
    ></lottie-player>
    <lottie-player
      src="https://assets9.lottiefiles.com/packages/lf20_zIOoIe.json"
      background="transparent"
      speed="1"
      style="width: 300px; height: 200px;position: absolute;
    bottom: 0; right:10px"
      loop
      autoplay
    ></lottie-player> -->

    <lottie-player
      @click="$vuetify.goTo(`#about-us`, options)"
      src="https://assets3.lottiefiles.com/packages/lf20_ADqq0Z.json"
      background="transparent"
      speed="1"
      style="width: 100px;
      height: 100px;
      bottom: 14px;
      position: absolute;
      left: 50%;
      margin-left: -50px;"
      loop
      autoplay
    ></lottie-player>
  </v-parallax>
</template>

<script>
import { mapState } from "vuex";

export default {
  data() {
    return {};
  },
  computed: {
    ...mapState(["arabicinfo"]),
    options() {
      return {
        duration: 1000,
        offset: 80,
        easing: "easeInOutCubic"
      };
    }
  }
};
</script>

<style lang="scss" scoped></style>
