<template>
  <v-card outlined class="rounded-xl cardadd">
    <v-toolbar flat color="transparent">
      <v-img max-height="65px" max-width="100px" src="logo2.png" eager></v-img>
      <v-spacer></v-spacer>
      <v-btn
        v-for="link in arabicinfo.header.links"
        :key="link.name"
        text
        class="mx-2 hidden-md-and-down transition-fast-in-fast-out"
        rounded
        nuxt
        v-ripple="{ class: `red--text` }"
        :medium="$vuetify.breakpoint.mdAndUp"
        :small="$vuetify.breakpoint.smAndDown"
        @click="$vuetify.goTo(link.to, options)"
      >
        <v-icon left>
          {{ link.icon }}
        </v-icon>
        {{ link.name }}
      </v-btn>

      <v-spacer></v-spacer>
      <v-btn
        class="hidden-lg-and-up "
        text
        fab
        :medium="$vuetify.breakpoint.mdAndUp"
        :small="$vuetify.breakpoint.smAndDown"
        @click="show = !show"
        v-ripple="{ class: `red--text` }"
      >
        <v-icon>{{ show ? "mdi-chevron-up" : "mdi-menu" }}</v-icon>
      </v-btn>
      <v-speed-dial v-model="fab" direction="bottom" :transition="transition">
        <template v-slot:activator>
          <v-tooltip bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                v-model="fab"
                text
                fab
                :medium="$vuetify.breakpoint.mdAndUp"
                :small="$vuetify.breakpoint.smAndDown"
                v-ripple="{ class: `red--text` }"
                v-on="$vuetify.breakpoint.mdAndUp ? on : {}"
                v-bind="attrs"
              >
                <v-icon v-if="fab">
                  mdi-close
                </v-icon>
                <v-icon v-else>
                  mdi-forum
                </v-icon>
              </v-btn>
            </template>
            <span>لتواصل معنا</span>
          </v-tooltip>
        </template>
        <v-btn
          href="tel: +967777203161"
          target="_blank"
          fab
          dark
          small
          color="green"
        >
          <v-icon>mdi-phone</v-icon>
        </v-btn>
        <v-btn
          href="//api.whatsapp.com/send?phone=+967777203161"
          target="_blank"
          fab
          dark
          small
          color="green"
          v-ripple="{ class: `red--text` }"
        >
          <v-icon>mdi-whatsapp</v-icon>
        </v-btn>

        <v-btn
          href="https://m.me/zaf3r.s"
          target="_blank"
          fab
          dark
          small
          color="accent"
          v-ripple="{ class: `red--text` }"
        >
          <v-icon>mdi-facebook-messenger</v-icon>
        </v-btn>

        <v-btn
          href="mailto: shakethi@info.com"
          target="_blank"
          fab
          dark
          small
          color="red"
          v-ripple="{ class: `red--text` }"
        >
          <v-icon>mdi-email</v-icon>
        </v-btn>
      </v-speed-dial>
      <v-tooltip bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            text
            fab
            :medium="$vuetify.breakpoint.mdAndUp"
            :small="$vuetify.breakpoint.smAndDown"
            @click="$vuetify.theme.dark = !$vuetify.theme.dark"
            v-bind="attrs"
            v-on="$vuetify.breakpoint.mdAndUp ? on : {}"
            v-ripple="{ class: `red--text` }"
          >
            <v-icon v-if="$vuetify.theme.dark">
              mdi-moon-waning-crescent
            </v-icon>
            <v-icon v-else>
              mdi-lightbulb-on
            </v-icon>
          </v-btn>
        </template>
        <span v-if="$vuetify.theme.dark">Dark</span>
        <span v-else>Light</span>
      </v-tooltip>
      <v-tooltip bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            text
            fab
            :medium="$vuetify.breakpoint.mdAndUp"
            :small="$vuetify.breakpoint.smAndDown"
            @click="$vuetify.rtl = !$vuetify.rtl"
            v-bind="attrs"
            v-on="$vuetify.breakpoint.mdAndUp ? on : {}"
            :to="$vuetify.rtl ? '/en' : '/'"
            v-ripple="{ class: `red--text` }"
          >
            <v-icon v-if="$vuetify.rtl">
              mdi-abjad-arabic
            </v-icon>
            <v-icon v-else>
              mdi-translate
            </v-icon>
          </v-btn>
        </template>
        <span v-if="$vuetify.rtl">عربي</span>
        <span v-else>English</span>
      </v-tooltip>
    </v-toolbar>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-row class="my-0 mx-0 py-4" justify="center">
          <v-btn
            v-for="link in arabicinfo.header.links"
            :key="link.name"
            text
            class="transition-fast-in-fast-out"
            rounded
            nuxt
            :medium="$vuetify.breakpoint.mdAndUp"
            :small="$vuetify.breakpoint.smAndDown"
            @click="$vuetify.goTo(link.to, options)"
            v-ripple="{ class: `red--text` }"
          >
            <v-icon left>
              {{ link.icon }}
            </v-icon>
            {{ link.name }}
          </v-btn>
        </v-row>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script>
import { mapState } from "vuex";
export default {
  data() {
    return {
      fab: false,
      show: false,
      transition: "slide-y-reverse-transition"
    };
  },

  computed: {
    options() {
      return {
        duration: 1000,
        offset: 80,
        easing: "easeInOutCubic"
      };
    },
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

<style lang="scss" scoped>
.cardadd {
  margin: 10px 2.5% 0px 2.5%;
  position: fixed;
  width: 95%;
  z-index: 5;
}
</style>
