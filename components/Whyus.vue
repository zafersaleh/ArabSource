<template>
  <v-container id="whyus" class="py-10">
    <v-row justify="center" class="ma-0">
      <v-col cols="12">
        <h1 class="text-h4 font-weight-black text-center">
          لماذا تختارنا
        </h1>
      </v-col>

      <v-col cols="12" md="5">
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
            v-for="(slide, i) in slides"
            :key="i"
            @mouseover="cycle = false"
            @mouseleave="cycle = true"
          >
            <v-img
              max-height="400px"
              max-width="400px"
              src="HealthCar.jpg"
              eager
            >
              <v-img
                max-height="400px"
                max-width="400px"
                src="shapeimage.png"
                eager
              ></v-img>
            </v-img>
          </v-carousel-item>
        </v-carousel>
      </v-col>
      <v-col cols="12" md="7">
        <v-carousel
          :continuous="false"
          :show-arrows="false"
          hide-delimiter-background
          delimiter-icon="mdi-blur"
          v-model="model"
          height="350px"
        >
          <v-carousel-item v-for="(slide, i) in slides" :key="i">
            <h1
              class="text-h4 font-weight-black my-10"
              @mouseover="cycle = false"
              @mouseleave="cycle = true"
            >
              أدوية بدون وصفة طبية
            </h1>
            <p
              class="text-body-2"
              @mouseover="cycle = false"
              @mouseleave="cycle = true"
            >
              الأدوية (OTC) هي الأدوية التي يمكن شراؤها بدون وصفة طبية. تستخدم
              هذه الأدوية في تخفيف أعراض الأمراض الشائعة مثل الام الجسم والحمى،
              تخفف هذه الأدوية من الصداع وألم الجسم والحكة، بينما تساعد بعض
              الأدوية على معالجة المشاكل المتكررة مثل الصداع النصفي والحساسية.
            </p>
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
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
    loop() {
      if (this.model === 4) {
        setTimeout(() => {
          this.model = 0;
        }, 3000);
      }
    }
  }
};
</script>

<style lang="scss">
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
