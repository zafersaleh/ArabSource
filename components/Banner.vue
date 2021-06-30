<template>
  <div id="hii" style="height:100vh;">
    <v-row
      align="center"
      justify="center"
      style="height:100%;position: relative;"
      class="ma-0"
    >
      <lottie-player
        src="bestcover.json"
        background="transparent"
        speed="1"
        style="
    position: absolute;
    width: 300px;
   height:300px;
   bottom:0px;
    z-index: 2;"
        :style="$vuetify.breakpoint.sm ? 'width: 450px;height:450px;' : ''"
        autoplay
        loop
      ></lottie-player>
      <v-col class="text-center mb-15" lg="5" md="7" cols="12">
        <v-img
          class="mb-5"
          style="margin:auto"
          max-height="100px"
          max-width="200px"
          src="logo2.png"
          eager
        ></v-img>
        <h4 class="subheading text-justify">
          {{ arabicinfo.header.description }}
        </h4>
      </v-col>
      <v-img
        v-if="$vuetify.breakpoint.mdAndUp"
        style="margin:auto; top:20px; position: absolute;  bottom:0px"
        src="lg-cover.png"
        eager
      ></v-img>
      <v-img
        v-if="$vuetify.breakpoint.sm"
        style="margin:auto; top:20px; position: absolute;  bottom:0px"
        src="sm-cover.png"
        eager
      ></v-img>
      <v-img
        v-if="$vuetify.breakpoint.xs"
        style="margin:auto; top:20px; position: absolute;  bottom:0px"
        src="xs-cover.png"
        eager
      ></v-img>
      <!-- <v-img
        v-if="$vuetify.breakpoint.mdAndDown"
        :width="$vuetify.breakpoint.xs ? '350px' : '460px'"
        :height="$vuetify.breakpoint.xs ? '270px' : '370px'"
        aspect-ratio="16:9"
        style=" position: absolute; bottom:25px "
        src="phone-cover.png"
        eager
      ></v-img> -->
    </v-row>
    <!-- 
    <lottie-player
      @click="$vuetify.goTo(`#about-us`, options)"
      src="line.json"
      background="red"
      speed="1"
      style="
      position: absolute;
      "
      autoplay
    ></lottie-player> -->
    <!-- <lottie-player
      src="co2.json"
      background="transparent"
      speed="1"
      style="position: absolute;top: -20%; width: 250px;left: 10%;"
      autoplay
      loop
    ></lottie-player>
    <lottie-player
      src="co1.json"
      background="transparent"
      speed="1"
      style="position: absolute;top: -20%; width: 250px;right: 10%;"
      autoplay
      loop
    ></lottie-player> -->
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  transition: "slide",
  data() {
    return {};
  },
  computed: {
    ...mapState(["arabic", "english"]),
    arabicinfo() {
      if (this.$vuetify.rtl) {
        return this.arabic;
      } else {
        return this.english;
      }
    },
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
