<template>
  <div class="search-container">
    <v-text-field
      v-model="search"
      @input="performSearch"
      label="Search for a movie"
      solo
      class="search-input"
      outlined
      placeholder="Enter a movie title..."
    >
      <template v-slot:append>
        <v-icon>mdi-movie</v-icon>
      </template>
    </v-text-field>

    <div v-if="films.length > 0" class="film-list">
      <h2 class="result-heading">Search Results</h2>
      <v-row class="films-container">
        <v-col cols="12" sm="6" md="4" lg="3" v-for="film in films" :key="film.imdbID">
          <v-card class="film-card" elevation="4">
            <v-img :src="film.Poster" alt="Movie Poster" class="film-poster"></v-img>
            <v-card-title class="film-details">
              <h3 class="film-title">{{ film.Title }}</h3>
              <p class="film-year">{{ film.Year }}</p>
              <v-btn :href="'https://www.imdb.com/title/' + film.imdbID" target="_blank" text class="imdb-link">IMDb Link</v-btn>
            </v-card-title>
          </v-card>
        </v-col>
      </v-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      films: []
    };
  },
  methods: {
    performSearch() {
      const api = `https://www.omdbapi.com/?apikey=421c5dbb&y=&s=${this.search}`;
      
      fetch(api)
        .then(response => response.json())
        .then(data => {
          this.films = data.Search || [];
        })
        .catch(error => {
          console.error("An error occurred during search:", error);
        });
    }
  }
};
</script>

<style scoped>
.search-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.search-input {
  margin-bottom: 20px;
}

.result-heading {
  font-size: 24px;
  color: #fcf9f9;
  text-align: center;
  margin-bottom: 20px;
}

.films-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  margin-top: 20px;
}

.film-card {
  width: 100%;
  border-radius: 10px;
  overflow: hidden;
  transition: transform 0.3s ease;
}

.film-card:hover {
  transform: translateY(-5px);
}

.film-poster {
  width: 100%;
  height: auto;
}

.film-details {
  padding: 15px;
  text-align: center;
}

.film-title {
  margin: 0;
  font-size: 18px;
}

.film-year {
  margin: 5px 0;
  color: #777;
}

.imdb-link {
  color: #921616;
  text-decoration: none;
  margin-top: 10px;
}

.imdb-link:hover {
  color: #921616;
}
</style>
