<script>
import MovieListItem from "@/compponent/movie-list-item/MovieListItem.vue";
export default {
  components: {MovieListItem},
  props: {
    movies: {
      type: Array,
      required: true,
    }
  }
}
</script>

<template>
  <div class="movie-list">
    <ul class="list-group">
<!--      <li v-for="movie in movies">{{ movie.name }}</li>-->
      <MovieListItem v-for="movie in movies" v-bind:movie="movie"/>
    </ul>
  </div>

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