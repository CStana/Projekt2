<template>
  <div class="home">
    <v-carousel cycle show-arrows-on-hover hide-delimiter-background>
      <template v-slot:prev="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" icon class="carousel-icon">
          <v-icon color="#921616">mdi-chevron-left</v-icon>
        </v-btn>
      </template>
      <template v-slot:next="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" icon class="carousel-icon">
          <v-icon color="#921616">mdi-chevron-right</v-icon>
        </v-btn>
      </template>
      <v-carousel-item
        v-for="film in filmovi"
        :key="film.imdbID"
        reverse-transition="fade-transition"
        transition="fade-transition"
      >
        <v-row textalign="center" justify="center">
          <v-col cols="1" sm="8" md="6" lg="4">
            <v-card target="blank" :href="film.url" class="film-card">
              <v-img :src="film.Poster" contain class="film-image"></v-img>
              <v-list-item three-line>
                <v-list-item-content>
                  <v-list-item-title>{{ film.Title }}</v-list-item-title>
                  <v-list-item-subtitle>{{ film.Year }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-card>
          </v-col>
        </v-row>
      </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  created() {
    this.dohvatiNajpopularnije();
  },
  data() {
    return {
      filmovi: ["Superman", "Batman", "Marvel"],
      slike: [],
    };
  },
  methods: {
    dohvatiNajpopularnije: function () {
      for (const film of this.filmovi) {
        this.axios
          .get(
            "https://www.omdbapi.com/?apikey=421c5dbb&y=&s=" + film
          )
          .then((response) => {
            this.filmovi = response.data.Search;
          });
      }
    },
  },
};
</script>

<style scoped>
.carousel-icon {
  font-size: 32px;
  padding: 0;
}

.film-card {
  background-color: transparent;
  border: none;
}

.film-image {
  max-height: 500px;
  width: auto;
}
</style>
