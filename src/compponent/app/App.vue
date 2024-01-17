<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo
          :allMoviesCount="movies.length"
          :favouriteMovieCount="movies.filter(c =>c.favourite).length"
      />
      <div class="search-panel">
        <SearchPanel :updateTermHandler="updateTermHandler"/>
        <AppFilter :updateFilterHandler="updateFilterHandler" :filterName="filter" />
      </div>
      <div class="movie-list" v-if="!movies.length && !isLoading">
        <p class="text-center fs-3 text-danger">Kinolar mavjud emas!</p>
      </div>
      <div class="movie-list d-flex justify-content-center" v-else-if="isLoading">
<!--        <div class="spinner-grow text-primary" role="status">-->
<!--          <span class="visually-hidden">Loading...</span>-->
<!--        </div>-->
<!--        <p class="text-center fs-3 text-danger">Kinolar yuklanmoqda...</p>-->
        <Loader />
      </div>
      <MovieList
          v-else
          :movies="onFilterHandler(onSearchHandler(movies, term), filter)"
          @onToggle="onToggleHandler"
          @onRemove="onRemoveHandler"
      />
      <div class="d-flex justify-content-center">
        <nav aria-label="pagination">
        <ul class="pagination pagination-sm">
          <li
              class="page-item"
              v-for="pageNumber in totalPages"
              :class="{active: pageNumber === page}"
              :key="pageNumber"
              @click="changePageHandler(pageNumber)"
          >
            <span class="page-link">{{ pageNumber }}</span>
          </li>
<!--          <li class="page-item active" aria-current="page">-->
<!--            <span class="page-link">1</span>-->
<!--          </li>-->
<!--          <li class="page-item"><a class="page-link" href="#">2</a></li>-->
<!--          <li class="page-item"><a class="page-link" href="#">3</a></li>-->
        </ul>
      </nav>
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
import axios from "axios";
import Loader from "@/ui/Loader.vue";

export default {
  components: {
    Loader,
    AppInfo,
    SearchPanel,
    AppFilter,
    MovieList,
    MovieAddForm,
  },
  data() {
    return {
      movies: [
        // {
        //   id: 1,
        //   name: 'Sayrga chiqgan go\'dak',
        //   viewers: 940,
        //   favourite: false,
        //   like: false,
        // },
        // {
        //   id: 2,
        //   name: 'Poyitaxt - Sulton Abdulhamidxon',
        //   viewers: 600,
        //   favourite: true,
        //   like: true,
        // },
        // {
        //   id: 3,
        //   name: 'Transformerlar - 2',
        //   viewers: 1501,
        //   favourite: false,
      ],
      term: '',
      filter: 'all',
      isLoading: false,
      limit: 10,
      page: 1,
      totalPages: 0,
    }
  },
  methods: {
    async createMovie(item) {
      const response = await axios.post('https://jsonplaceholder.typicode.com/posts', item)
      console.log(response)
      this.movies.push(response.data)
    },
    onToggleHandler({id, prop}) {
      this.movies = this.movies.map(item => {
        if (item.id === id) {
          return {...item, [prop]: !item[prop]}
        }
        return item
      })
    },
    onRemoveHandler(id) {
      this.movies = this.movies.filter(c => c.id !== id)
    },
    onSearchHandler(arr, term) {
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

    updateFilterHandler(filter) {
      this.filter = filter
    },

    async fetchMovie() {
      // const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
      try {
        this.isLoading = true
        // setTimeout(async () =>{
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
          params: {
            _limit: this.limit,
            _page: this.page
          }
        })
        // const response = await axios.get('https://student.namdu.uz/rest/v11/public/university-list')
        const newArr = response.data.map(item => ({
          id: item.id,
          name: item.title,
          like: false,
          favourite: false,
          viewers: item.id * 150,
        }))
        this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit )
        this.movies = newArr
        // this.isLoading = false
        // }, 3000)

      } catch (error) {
        alert(error.message)
      } finally {
        this.isLoading = false
      }
    },

    changePageHandler(page) {
      this.page = page
    },

  },
  mounted() {
    this.fetchMovie()
  },
  watch: {
    page() {
      this.fetchMovie()
    },
  }
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