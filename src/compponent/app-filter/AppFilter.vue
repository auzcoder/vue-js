<script>
export default {
  updateFilterHendler: {
    type: Function,
    required: true,
  },
  data() {
    return {
      filter: 'all',
    }
  },
}
</script>

<template>
  <div class="btn-group">
    <button class="btn btn-outline-primary" type="button">
      Barcha kinolar
    </button>
    <button class="btn btn-outline-primary" type="button">
      Mashhur kinolar
    </button>
    <button class="btn btn-outline-primary" type="button">
      Eng ko'p ko'rilgan kinolar
    </button>
  </div>
</template>

<style scoped>

</style>