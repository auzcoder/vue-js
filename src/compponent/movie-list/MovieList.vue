<script>
import MovieListItem from "@/compponent/movie-list-item/MovieListItem.vue";
export default {
  components: {MovieListItem},
  data() {
    return {
      movies: [
        {
          name: 'Sayrga chiqgan go\'dak',
          viewers: 940,
          favourite: false,
          like: false,
        },
        {
          name: 'Poyitaxt - Sulton Abdulhamidxon',
          viewers: 600,
          favourite: true,
          like: true,
        },
        {
          name: 'Transformerlar - 2',
          viewers: 1501,
          favourite: false,
          like: false,
        },
        {
          name: 'Uyda yog\'iz - 4',
          viewers: 420,
          favourite: false,
          like: false
        },
        {
          name: 'Ichkarida - Turk seriali',
          viewers: 420,
          favourite: true,
          like: true
        },
      ],
    }
  },
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