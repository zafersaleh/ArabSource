<template>
  <v-container id="about-us" class="py-10">
    <v-row justify="center" class="ma-0">
      <v-col cols="12">
        <h1 class="text-h4 font-weight-black text-center">
          {{ arabicinfo.aboutus.title }}
        </h1>
      </v-col>
      <v-col cols="12" class="text-center">
        <h1 class="text-subtitle-1 text-justify">
          {{ arabicinfo.aboutus.description }}
        </h1>
      </v-col>
      <v-col
        cols="12"
        md="4"
        v-for="data in arabicinfo.aboutus.mores"
        :key="data.name"
        style="height: auto"
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
            <p style="text-align: justify;" class=" text-body-2">
              {{ data.details }}
            </p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from "vuex";

export default {
  computed: {
    ...mapState(["arabicinfo"])
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
