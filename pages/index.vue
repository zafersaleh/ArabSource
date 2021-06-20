<template>
  <div>
    <Banner />
    <About />
    <ServiceOne />

    <Whyus />
  </div>
</template>

<script>
import Banner from "@/components/Banner.vue";
import ServiceOne from "@/components/ServiceOne.vue";
import ServiceTwo from "@/components/ServiceTwo.vue";
import About from "@/components/About.vue";
import Whyus from "@/components/Whyus.vue";

export default {
  components: {
    Whyus,
    About,
    ServiceTwo,
    ServiceOne,
    Banner
  }
};
</script>

<style lang="scss" scoped></style>
