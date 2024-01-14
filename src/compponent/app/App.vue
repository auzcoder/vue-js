<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo
          :allMoviesCount="movies.length"
          :favouriteMovieCount="movies.filter(c =>c.favourite).length"
      />
      <div class="search-panel">
        <SearchPanel :updateTermHandler="updateTermHandler"/>
        <AppFilter />
      </div>
      <div class="movie--list">
        <MovieList
            :movies="onFilterHandler(onSearchHendler(movies, term), filter)"
            @onToggle="onToggleHandler"
            @onRemove="onRemoveHandler"
        />
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
          id: 1,
          name: 'Sayrga chiqgan go\'dak',
          viewers: 940,
          favourite: false,
          like: false,
        },
        {
          id: 2,
          name: 'Poyitaxt - Sulton Abdulhamidxon',
          viewers: 600,
          favourite: true,
          like: true,
        },
        {
          id: 3,
          name: 'Transformerlar - 2',
          viewers: 1501,
          favourite: false,
          like: false,
        },
        {
          id: 4,
          name: 'Uyda yog\'iz - 4',
          viewers: 420,
          favourite: false,
          like: false
        },
        {
          id: 5,
          name: 'Ichkarida - Turk seriali',
          viewers: 420,
          favourite: true,
          like: true
        },
      ],
      term: '',
      filter: 'all',
    }
  },
  methods: {
    createMovie(item) {
      this.movies.push(item)
    },
    onToggleHandler({id, prop}) {
      this.movies = this.movies.map(item => {
        if (item.id === id) {
          console.log(item)
          return {...item, [prop]: !item[prop]}
        }
        return item
      })
    },
    onRemoveHandler(id) {
      this.movies = this.movies.filter(c => c.id !== id)
    },
    onSearchHendler(arr, term) {
      if(term.length === 0){
        return arr
      }
      return arr.filter(c => c.name.toLowerCase().indexOf(term) > -1)
    },
    onFilterHandler(arr, filter) {
      switch (filter) {
        case "popular":
          return arr.filter(c => c.like)
        case "mostViewers":
          return arr.filter(c => c.viewers > 500)
        default:
          return arr
      }
    },

    updateTermHandler(term) {
      this.term = term
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

/*.movie-list {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}*/
</style>