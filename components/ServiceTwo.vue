<template>
  <v-container class="py-10">
    <v-row justify="center">
      <v-col cols="12" class="text-center">
        <h1 class="subheading text-h5 font-weight-black my-4">about us</h1>
      </v-col>
      <v-col md="8" cols="12">
        <v-expansion-panels popout v-model="panel" tile multiple>
          <v-expansion-panel v-for="(item, i) in items" :key="i">
            <v-expansion-panel-header
              >Header {{ item }}</v-expansion-panel-header
            >
            <v-expansion-panel-content>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
              eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut
              enim ad minim veniam, quis nostrud exercitation ullamco laboris
              nisi ut aliquip ex ea commodo consequat.
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      items: 5,
      panel: [1, 2]
    };
  }
};
</script>

<style lang="scss" scoped></style>
