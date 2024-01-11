<script>
export default {
  props: {
    allMoviesCount: {
      type: Number,
      required: true,
    },
    favouriteMovieCount: {
      type: Number,
      required: true,
    }
  },
}
</script>

<template>
  <div class="app-info">
    <p class="fs-3 text-uppercase">Barcha kinolar soni: {{ allMoviesCount }}</p>
    <p class="fs-4 text-uppercase">Ko'rilgan kinolar soni: {{ favouriteMovieCount }}</p>
  </div>
</template>

<style scoped>
.app-info {
  margin-top: 1.5rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>