<template>
  <div class="my-20">
    <v-app-bar
      app
      flat
      absolute
      :height="height"
      class="ma-0 pa-0"
      color="primary"
      floating
    >
      <v-toolbar-title>Title</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        v-for="link in links"
        :key="link.name"
        text
        class="mx-2 hidden-sm-and-down transition-fast-in-fast-out"
        rounded
        :to="link.to"
        nuxt
        large
      >
        <v-icon left>
          {{ link.icon }}
        </v-icon>
        {{ link.name }}
      </v-btn>

      <v-spacer></v-spacer>
      <v-btn
        class="hidden-md-and-up"
        text
        fab
        :medium="$vuetify.breakpoint.mdAndUp"
        :small="$vuetify.breakpoint.smAndDown"
        @click="show = !show"
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
                v-ripple="{ class: `secondary--text` }"
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
        <v-btn fab dark small color="accent">
          <v-icon>mdi-facebook-messenger</v-icon>
        </v-btn>
        <v-btn fab dark small color="green">
          <v-icon>mdi-whatsapp</v-icon>
        </v-btn>
        <v-btn fab dark small color="green">
          <v-icon>mdi-android-messages</v-icon>
        </v-btn>
        <v-btn fab dark small color="red">
          <v-icon>mdi-email</v-icon>
        </v-btn>
      </v-speed-dial>
      <v-btn
        text
        fab
        :medium="$vuetify.breakpoint.mdAndUp"
        :small="$vuetify.breakpoint.smAndDown"
        @click="$vuetify.theme.dark = !$vuetify.theme.dark"
      >
        <v-icon v-if="$vuetify.theme.dark">
          mdi-lightbulb-on
        </v-icon>
        <v-icon v-else>
          mdi-lightbulb
        </v-icon>
      </v-btn>
      <v-btn
        text
        fab
        :medium="$vuetify.breakpoint.mdAndUp"
        :small="$vuetify.breakpoint.smAndDown"
        @click="$vuetify.rtl = !$vuetify.rtl"
      >
        <v-icon v-if="$vuetify.rtl">
          mdi-translate
        </v-icon>
        <v-icon v-else>
          mdi-abjad-arabic
        </v-icon>
      </v-btn>
    </v-app-bar>
    <v-card :style="navh" class="mb-0 mx-0" elevation="1" tile>
      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-row class="my-0 mx-0 py-4" justify="center" align="center">
            <v-btn
              v-for="link in links"
              :key="link.name"
              text
              class="mx-2 transition-fast-in-fast-out"
              rounded
              :to="link.to"
              nuxt
              large
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
  </div>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      links: [
        { name: "الرئيسة", icon: "mdi-home", to: "/" },
        { name: "من نحن", icon: "mdi-shopping", to: "/product" },
        { name: "خدماتنا", icon: "mdi-shopping", to: "/product" },
        { name: "لماذا نحن", icon: "mdi-shopping", to: "/product" },
        { name: "تواصل معنا", icon: "mdi-shopping", to: "/product" }
      ],
      fab: false,
      transition: "slide-y-reverse-transition",
      selectedmoney: 0,
      selectedtheme: 0,
      mode: false,
      show: false
    };
  },
  computed: {
    logo() {
      return (
        "height:calc(" +
        this.height +
        " - 10px);" +
        "width:calc(" +
        this.height +
        " - 10px);"
      );
    },
    height() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
          return "70px";
        case "sm":
          return "70px";
        case "md":
          return "90px";
        case "lg":
          return "100px";
        case "xl":
          return "120px";
      }
    },
    navh() {
      return "margin-top: " + this.height + ";";
    }
  }
};
</script>

<style lang="scss" scoped>
a {
  margin: 0;
  padding: 0;
  text-decoration: none;
  color: #ffffff;
}
.v-btn:before {
  background-color: transparent;
}
</style>
