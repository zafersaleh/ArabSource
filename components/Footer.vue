<template>
  <v-footer padless>
    <v-card class="flex" flat tile>
      <v-divider class="mx-10"></v-divider>
      <v-divider class="mx-10 mt-1"></v-divider>
      <v-container class="pt-10">
        <v-row justify="space-between" class="ma-0">
          <v-col cols="12" md="5">
            <h1 class="subheading text-h5 font-weight-black mb-5">
              {{ arabicinfo.aboutus.title }}
            </h1>
            <p style="text-align: justify;" class="text-caption mx-2">
              {{ arabicinfo.header.description }}
            </p>

            <h1 class="subheading text-h6 font-weight-blac kmy-5">
              {{ arabicinfo.footer.title }}
            </h1>
            <p class="text-caption mx-2">
              {{ arabicinfo.footer.more }}
            </p>
            <div class="d-flex evenly mt-4">
              <v-btn
                v-for="link in arabicinfo.footer.contact"
                :key="link.icon"
                :href="link.link"
                target="_blank"
                fab
                small
                rounded
                :color="link.color"
                class="mx-2 mt-3"
              >
                <v-icon>{{ link.icon }}</v-icon>
              </v-btn>
            </div>
          </v-col>
          <v-col cols="12" md="3">
            <h1 class="subheading text-h6 font-weight-black my-2">
              {{ arabicinfo.footer.menu }}
            </h1>
            <v-list nav dense>
              <v-list-item
                v-for="(item, i) in arabicinfo.header.links"
                :key="i"
                @click="$vuetify.goTo(item.to, options)"
                v-ripple="{ class: `red--text` }"
              >
                <v-list-item-icon>
                  <v-icon v-text="item.icon"></v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                  <v-list-item-title v-text="item.name"></v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-col>
          <v-col cols="12" md="3">
            <h1 class="subheading text-h6 font-weight-black mb-5">
              {{ arabicinfo.footer.follow }}
            </h1>
            <div class="d-flex evenly mt-2">
              <v-btn
                v-for="socail in arabicinfo.footer.socail"
                :key="socail.icon"
                :href="socail.link"
                target="_blank"
                fab
                small
                rounded
                color="red"
                class="mx-2 white--text"
              >
                <v-icon>{{ socail.icon }}</v-icon>
              </v-btn>
            </div>
            <div
              v-if="$vuetify.breakpoint.mdAndUp"
              class="d-flex justify-md-end mt-15"
            >
              <v-btn
                color="red"
                large
                outlined
                rounded
                :medium="$vuetify.breakpoint.mdAndUp"
                :small="$vuetify.breakpoint.smAndDown"
                @click="$vuetify.theme.dark = !$vuetify.theme.dark"
                class="mx-1"
              >
                <span v-if="$vuetify.theme.dark">Dark</span>
                <span v-else>Light</span>
                <v-icon right v-if="$vuetify.theme.dark">
                  mdi-moon-waning-crescent
                </v-icon>
                <v-icon right v-else>
                  mdi-lightbulb-on
                </v-icon>
              </v-btn>

              <v-btn
                color="red"
                large
                outlined
                rounded
                :medium="$vuetify.breakpoint.mdAndUp"
                :small="$vuetify.breakpoint.smAndDown"
                @click="$vuetify.rtl = !$vuetify.rtl"
                class="mx-2"
              >
                <span v-if="$vuetify.rtl">عربي</span>
                <span v-else>English</span>
                <v-icon right v-if="$vuetify.rtl">
                  mdi-abjad-arabic
                </v-icon>
                <v-icon v-else right>
                  mdi-translate
                </v-icon>
              </v-btn>
            </div>
          </v-col>
        </v-row>
      </v-container>

      <v-divider></v-divider>
      <p class="py-2 ma-0 text-Subtitle-1 font-weight-black   text-center">
        copyright© {{ new Date().getFullYear() }} ArabRrsource
      </p>
    </v-card>
  </v-footer>
</template>

<script>
import { mapState } from "vuex";

export default {
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
      icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
      duration: 1000,
      offset: 0,
      easing: "easeInOutCubic"
    };
  }
};
</script>

<style lang="scss">
.heightcol {
  height: 320px;
}
.mapouter {
  position: relative;
  text-align: right;
  height: 250px;
  width: 350px;
}
.evenly {
  justify-content: space-evenly;
}
.theme--light.v-list {
  background: transparent !important;
}
.theme--dark.v-list {
  background: transparent !important;
}
</style>
