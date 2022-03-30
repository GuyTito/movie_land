<script setup>
import { computed } from "@vue/reactivity";

const props = defineProps(['movie', ])

const movie_poster = computed(()=>{
  return props.movie.Poster !== 'N/A' ? props.movie.Poster : 'https://via.placeholder.com/400'
})

</script>


<template>
  <div class="movie">
    <div>
      <p>{{ movie.Year }}</p>
    </div>

    <div>
      <img :src="movie_poster" :alt="movie.Title" />
    </div>

    <div>
      <span>{{ movie.Type }}</span>
      <h3>{{ movie.Title }}</h3>
    </div>
  </div>
</template>


<style lang="scss" scoped>
</style>