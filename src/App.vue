<template>
  <v-app>
    <v-main class="d-flex">
      <v-card
        class="d-flex flex-column text-center justify-center align-center main-card py-6 px-6 px-md-12"
        theme="dark"
        elevation="1"
        rounded="20"
      >
        <div class="d-flex my-4">
          <div class="d-flex flex-column mx-3 mx-md-6">
            <div class="text-h3 text-md-h2 font-weight-bold">
              {{ parseInt(timediff / (24 * 3600)) }}
            </div>
            <div class="text-h5">Days</div>
          </div>
          <div class="d-flex flex-column mx-3 mx-md-6">
            <div class="text-h3 text-md-h2 font-weight-bold">
              {{ parseInt((timediff % (24 * 3600)) / 3600) }}
            </div>
            <div class="text-h5">Hours</div>
          </div>
          <div class="d-flex flex-column mx-3 mx-md-6">
            <div class="text-h3 text-md-h2 font-weight-bold">
              {{ parseInt((timediff % (24 * 60)) / 60) }}
            </div>
            <div class="text-h5">Minutes</div>
          </div>
        </div>
        <v-container style="max-width: 500px">
          <v-progress-linear
            color="rgba(255, 255, 255, 0.6)"
            :model-value="parseInt(timediff % 60)"
            max="60"
            height="2"
            class="mb-6"
          ></v-progress-linear>
        </v-container>
        <div class="text-h5">since&nbsp;@YukariChiba started&nbsp;HRT</div>
        <div class="mt-8 mb-8 d-flex">
          <div class="mx-2">
            <v-icon size="x-large">mdi-debian</v-icon>
            <v-icon size="x-large">mdi-package</v-icon>
            x {{ parseInt(timediff / (6 * 3600) / 21) }}
          </div>
          <v-icon size="x-large">mdi-plus</v-icon>
          <div class="mx-2">
            <v-icon size="x-large">mdi-debian</v-icon>
            <v-icon size="x-large">mdi-pill</v-icon> x
            {{ parseInt(timediff / (6 * 3600)) % 21 }}
          </div>
        </div>
      </v-card>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},
  created() {
    const self = this;
    setInterval(() => {
      self.timediff = (new Date() - self.start_date) / 1000;
    }, 1000);
  },
  data: () => ({
    start_date: 1632671880000,
    timediff: 0,
  }),
};
</script>
