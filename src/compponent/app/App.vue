<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo />
      <div class="search-panel">
        <SearchPanel />
        <AppFilter />
      </div>
      <div class="">
        <MovieList />
      </div>

      <MovieAddForm />
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
</style>