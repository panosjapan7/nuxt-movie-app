<template>
  <div class="home">
    <Hero />
  </div>
</template>

<script>
import axios from "axios"
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
      const data = axios.get("https://api.themoviedb.org/3/movie/now_playing?api_key=238cb64db6302e7587f0099a49af4b3d&language=en-US$page=1")
      const result = await data
      result.data.results.forEach(movie => {
        this.movies.push(movie)
      })
      console.log(this.movies)
    }
  }
}
</script>
