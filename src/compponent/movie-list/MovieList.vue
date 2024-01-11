<script setup>

import MovieListItem from "@/compponent/movie-list-item/MovieListItem.vue";
</script>

<template>
  <ul class="movie-list list-group">
    <MovieListItem />
  </ul>
</template>

<style scoped>
.movie-list {
  margin-bottom: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>