<template>
  <v-container
    v-animate-onscroll="{ down: 'animated fadeInUp' }"
    id="Agents"
    class="py-10"
  >
    <v-row justify="center" class="ma-0">
      <v-col cols="12">
        <h1
          v-animate-onscroll="{ down: 'animated pulse' }"
          class="text-h5 font-weight-black text-center"
        >
          {{ arabicinfo.agents.title }}
        </h1>
      </v-col>
      <v-col cols="12" sm="10" md="10">
        <v-card style="border-color:red" outlined>
          <v-card-text class="text-subtitle-1">
            {{ arabicinfo.agents.description }}
          </v-card-text>
        </v-card>
      </v-col>
      <v-col class="mx-0" sm="10" cols="12" md="2">
        <v-btn
          :height="$vuetify.breakpoint.smAndDown ? '' : '100%'"
          color="red"
          large
          outlined
          block
          href="mailto: shakethi@info.com"
        >
          <span v-if="this.$vuetify.rtl" class="text-subtitle-1">
            توصلوا معنا
          </span>
          <span v-else class="text-subtitle-1">
            Contact US
          </span>
          <v-icon size="25px" right>
            mdi-email
          </v-icon>
        </v-btn>
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
    }
  }
};
</script>

<style lang="scss"></style>
