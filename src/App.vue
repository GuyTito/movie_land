<script setup>
import SearchIcon from "@/assets/search.svg"
import { ref } from "vue";
import MovieCard from "./components/MovieCard.vue";

const API_URL = 'http://www.omdbapi.com/?apikey=C032E2D7'
const movies = ref([])
const searchTerm = ref('')

const searchMovies = async (title) => {
  const res = await fetch(`${API_URL}&s=${title}`)
  const data = await res.json()

  movies.value = data.Search
  searchTerm.value = ''
}
searchMovies('spiderman')

</script>


<template>
  <div class="app">
    <h1>MovieLand</h1>

    <form @submit.prevent="searchMovies(searchTerm)" class="search">
      <input v-model="searchTerm" type="text" placeholder="Search for movies" />
      <button>
        <img :src="SearchIcon" alt="search" @click="">
      </button>
    </form>

    <div v-if="movies.length" class="container">
      <template v-for="movie in movies" :key="movie.imdbID">
        <MovieCard :movie="movie" />
      </template>
    </div>
    <div v-else class="empty">
      <h2>No movies found</h2>
    </div>
  </div>
</template>


<style scoped>
button{
  background-color: transparent;
}
</style>