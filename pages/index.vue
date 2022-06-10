<template>
  <div class="home">
    <HeroComponent />
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
      console.log(result.data)
    }
  },
}
</script>
