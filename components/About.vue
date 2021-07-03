<template>
  <div style="box-shadow: -0px -3px 5px #CCC">
    <v-container
      v-animate-onscroll="{ down: 'animated fadeInUp' }"
      style="position: relative"
      id="about-us"
      class="mb-10 pb-10 pt-20"
    >
      <lottie-player
        src="ab1.json"
        background="transparent"
        speed="1"
        style="position: absolute;top:0px; right:0px"
        :style="
          $vuetify.breakpoint.xs
            ? 'width: 150px;height: 150px'
            : 'width: 200px;height: 200px'
        "
        autoplay
        loop
      ></lottie-player>
      <lottie-player
        src="ab1.json"
        background="transparent"
        speed="1"
        style="position: absolute;top: 0px;left:0px"
        :style="
          $vuetify.breakpoint.xs
            ? 'width: 150px;height: 150px'
            : 'width: 200px;height: 200px'
        "
        autoplay
        loop
      ></lottie-player>
      <v-row justify="center" class="ma-0">
        <v-col cols="8" class="my-5">
          <h1
            v-animate-onscroll="{ down: 'animated pulse' }"
            class="text-h4  font-weight-black text-center"
          >
            {{ arabicinfo.aboutus.title }}
          </h1>
        </v-col>
        <v-col
          cols="12"
          lg="9"
          md="10"
          sm="10"
          class="text-center"
          style="z-index: 3;"
        >
          <v-card style="border-color:red" outlined>
            <v-card-text class="text-subtitle-1 text-justify">
              {{ arabicinfo.aboutus.description }}
            </v-card-text>
          </v-card>
        </v-col>
        <v-col
          cols="12"
          lg="4"
          md="6"
          sm="10"
          v-for="data in arabicinfo.aboutus.mores"
          :key="data.name"
          style="height: auto;z-index: 3;"
        >
          <v-card elevation="1" shaped style="height: 100%">
            <lottie-player
              :src="data.icon"
              background="transparent"
              speed="1"
              style="width: 100px; height: 100px;  margin: auto;"
              loop
              autoplay
            ></lottie-player>

            <v-card-title style="justify-content: center;height: 70px">{{
              data.name
            }}</v-card-title>
            <v-card-text>
              <p
                v-html="data.details"
                style="text-align: justify;"
                class=" text-body-2"
              ></p>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  transition: "slide",
  computed: {
    ...mapState(["arabic", "english"]),
    arabicinfo() {
      if (this.$vuetify.rtl) {
        return this.arabic;
      } else {
        return this.english;
      }
    }
  },
  data() {
    return {
      datas: [
        { title: "Click Me" },
        { title: "Click Me" },
        { title: "Click Me" }
      ]
    };
  }
};
</script>

<style lang="scss" scoped></style>
