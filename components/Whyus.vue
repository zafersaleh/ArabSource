<template>
  <v-container
    v-animate-onscroll="{ down: 'animated fadeInUp' }"
    id="whyus"
    class="py-10"
  >
    <v-row justify="center" class="ma-0">
      <v-col cols="12">
        <h1
          v-animate-onscroll="{ down: 'animated pulse' }"
          class="text-h4 font-weight-black text-center"
          v-html="arabicinfo.whyus.title"
        ></h1>
      </v-col>

      <v-col style="position: relative;" cols="12" sm="8" md="5">
        <v-img
          class="moveup"
          max-height="400px"
          max-width="400px"
          src="whycover.png"
          style="position: absolute;left: 0px;right: 0px;z-index: 3;"
        ></v-img>

        <v-carousel
          :cycle="cycle"
          interval="3000"
          :continuous="false"
          :show-arrows="false"
          hide-delimiter-background
          hide-delimiters
          height="auto"
          v-model="model"
          v-on:change="loop"
        >
          <v-carousel-item
            v-for="(slide, i) in arabicinfo.whyus.mores"
            :key="i"
            @mouseover="cycle = false"
            @mouseleave="cycle = true"
          >
            <v-img
              max-height="350px"
              max-width="350px"
              :src="slide.image"
              eager
            ></v-img>
          </v-carousel-item>
        </v-carousel>
      </v-col>
      <v-col cols="12" sm="10" md="7">
        <v-carousel
          :continuous="false"
          :show-arrows="false"
          hide-delimiter-background
          delimiter-icon="mdi-blur"
          v-model="model"
          height="350px"
        >
          <v-carousel-item
            v-for="(slide, i) in arabicinfo.whyus.mores"
            :key="i"
          >
            <h1
              class="text-h4 font-weight-black my-10"
              @mouseover="cycle = false"
              @mouseleave="cycle = true"
            >
              {{ slide.name }}
            </h1>
            <p
              class="text-body-2"
              @mouseover="cycle = false"
              @mouseleave="cycle = true"
            >
              {{ slide.details }}
            </p>
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from "vuex";

export default {
  data() {
    return {
      colors: [
        "green",
        "secondary",
        "yellow darken-4",
        "red lighten-2",
        "orange darken-1"
      ],
      cycle: true,
      slides: ["First", "Second", "Third", "Fourth", "Fifth"],
      model: 0
    };
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
    loop() {
      if (this.model === 6) {
        setTimeout(() => {
          this.model = 0;
        }, 3000);
      }
    }
  }
};
</script>

<style lang="scss">
.moveup {
  animation: mover 1s infinite alternate;
}
@keyframes mover {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-10px);
  }
}
.shape {
  position: relative;
  background-color: red;
  width: 350px;
  height: 360px;
  margin-left: auto;
  margin-right: auto;
  border-top-left-radius: 60px;
  border-top-right-radius: 60px;
  position: relative;
}
.v-btn--icon {
  color: red !important;
}
</style>
