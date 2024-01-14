<script>
export default {
  updateFilterHandler: {
    type: Function,
    required: true,
  },
  data() {
    return {
      filter: 'all',
    }
  },
  methods: {
    filterHandler(filter) {
      this.filter = filter
      this.updateFilterHandler(this.filter)
    }
  }
}
</script>

<template>
  <div class="btn-group">
    <button class="btn btn-outline-primary" type="button" @click="filterHandler('all')">
      Barcha kinolar
    </button>
    <button class="btn btn-outline-primary" type="button" @click="filterHandler('popular')">
      Mashhur kinolar
    </button>
    <button class="btn btn-outline-primary" type="button" @click="filterHandler('mostViewers')">
      Eng ko'p ko'rilgan kinolar
    </button>
  </div>
</template>

<style scoped>

</style>