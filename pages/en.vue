<template>
  <div>
    <Banner />
    <About />
    <ServiceOne />
    <Agents />
    <Whyus />
  </div>
</template>

<script>
import Banner from "@/components/Banner.vue";
import ServiceOne from "@/components/ServiceOne.vue";
import About from "@/components/About.vue";
import Whyus from "@/components/Whyus.vue";
import Agents from "@/components/Agents.vue";
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
  head() {
    return {
      title: this.arabicinfo.header.title,
      htmlAttrs: {
        lang: this.$vuetify.rtl ? "ar" : "en"
      },
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.arabicinfo.header.description
        }
      ]
    };
  },
  beforeCreate() {
    this.$vuetify.rtl = false;
  },
  components: {
    Agents,
    Whyus,
    About,
    ServiceOne,
    Banner
  }
};
</script>

<style lang="scss" scoped></style>
