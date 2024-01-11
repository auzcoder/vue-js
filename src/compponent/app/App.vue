<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo
          :allMoviesCount="movies.length"
          :favouriteMovieCount="movies.filter(c =>c.favourite).length"
      />
      <div class="search-panel">
        <SearchPanel />
        <AppFilter />
      </div>
      <div class="movie--list">
        <MovieList :movies="movies" />
      </div>

      <MovieAddForm  @createMovie="createMovie" />
    </div>

  </div>

</template>
<script>
import AppInfo from "@/compponent/app-info/AppInfo.vue";
import SearchPanel from "@/compponent/search-panel/SearchPanel.vue";
import AppFilter from "@/compponent/app-filter/AppFilter.vue";
import MovieList from "@/compponent/movie-list/MovieList.vue";
import MovieAddForm from "@/compponent/movie-add-form/MovieAddForm.vue";

export default {
  components: {
    AppInfo,
    SearchPanel,
    AppFilter,
    MovieList,
    MovieAddForm,
  },
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
  methods: {
    createMovie(item) {
      this.movies.push(item)
    },
  },
}


</script>

<style>
.app{
  height: 100vh;
  color: #000;
}
.content {
  width: 1000px;
  min-height: 700px;
  background-color: #ffff;
  margin: 0 auto;
  padding: 5rem 0;
}

.search-panel {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}

.movie-list {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>