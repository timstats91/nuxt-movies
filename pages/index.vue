<template>
  <div class="home">

    <!-- Hero -->
    <HeroComponent />

    <!-- Movies -->
    <div class="container movies">
      <div id="user-grid" class="movie-grid">
        <div class="movie" v-for="(movie, index) in movies" :key="index">
          <div class="movie-img">
            <img :src="`https://tmdb.org/t/p/${movie.poster_path}`" alt="">
            <p class="review">{{movie.vote_average}}</p>
            <p class="overview">{{movie.overview}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      movies: [],
    }
  },
  async fetch() {
    await this.getMovies()
  },
  methods: {
    async getMovies() {
      const data = axios.get(
        'https://api.themoviedb.org/3/movie/550?api_key=d4be5df613286799989a0a84c536f851&language=en-US&page=1'
      )
      const result = await data
      result.data.results.forEach((movie) => {
        this.movies.push(movie)
      })
      console.log(this.movies)
    },
  },
}
</script>
