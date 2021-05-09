<template>
  <v-app class="grey">
    <v-main>
      <v-container fluid class="grey lighten-2" fill-height>
        <v-row>
          <v-col align="center">
            <v-sheet
              width="300"
              elevation="2"
              rounded
              color="white "
              class="pa-10"
            >
              <div v-if="loading">
                <v-row>
                  <v-col class="display-2 mt-3 text-center font-weight-normal">
                    {{ data[0].city_name }}</v-col
                  >
                </v-row>
                <v-row>
                  <v-col class="mt-n3">{{ data[0].weather.description }}</v-col>
                </v-row>
                <v-row class="d-flex">
                  <v-col class="d-flex justify-center align-center"
                    ><img :src="src" alt=""
                  /></v-col>
                  <v-col
                    class="font-weight-regular d-flex justify-center align-center display-2"
                    >{{ Math.round(data[0].temp) }}&#730;</v-col
                  >
                </v-row>
                <v-row>
                  <v-col class="ml-3">
                    <div class="d-flex flex-row align-center ">
                      <v-img
                        src="../src/assets/humidity.png"
                        max-height="30"
                        max-width="30"
                      ></v-img>
                      <v-icon>mdi-WaterPercent</v-icon>
                      <div class="mx-3">{{ Math.round(data[0].rh) }}</div>
                    </div>
                  </v-col>
                  <v-col class="ml-6">
                    <div class="d-flex flex-row align-center justify-center ">
                      <v-img
                        src="../src/assets/wind.jpg"
                        max-height="40"
                        max-width="40"
                      ></v-img>
                      <v-icon>mdi-WaterPercent</v-icon>
                      <div class="mx-3">{{ Math.round(data[0].wind_spd) }}</div>
                    </div>
                  </v-col>
                </v-row>
              </div>
              <div v-else>
                <v-progress-circular indeterminate color="primary">
                </v-progress-circular>
              </div>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",
  components: {},

  data: () => ({
    data: [],
    loading: false,
    //
  }),
  methods: {
    async getData() {
      var res = await fetch(
        "https://api.weatherbit.io/v2.0/current?lat=15.590041405106799&lon=32.561506758780354&key=2f63e933c3094e8bb8b14b891643c802	&include=minutely"
      );
      res = await res.json();
      this.data = res.data;
      this.loading = true;
    },
  },
  created() {
    this.getData();
  },
  computed: {
    src() {
      return `https://www.weatherbit.io/static/img/icons/${this.data[0].weather.icon}.png`;
    },
  },
};
</script>
