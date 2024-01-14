<script>
export default {
  props: {
    updateFilterHandler: {
      type: Function,
      required: true,
    },
  },
  filterName: {
    type: String,
    required: true,
  },
  data() {
    return {
      filterButtons: [
        {
          title: 'Barcha kinolar',
          name: 'all'
        },
        {
          title: 'Mashhur kinolar',
          name: 'popular'
        },
        {
          title: 'Eng ko\'p ko\'rilgan kinolar',
          name: 'mostViewers'
        },
      ],
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
    <button
        class="btn"
        type="button"
        @click="filterHandler('all')"
        :class="[filterName === 'all' ? 'btn-primary' : 'btn-outline-primary']"
    >
      Barcha kinolar
    </button>
    <button
        class="btn"
        type="button"
        @click="filterHandler('popular')"
        :class="[filterName === 'popular' ? 'btn-primary' : 'btn-outline-primary']"
    >
      Mashhur kinolar
    </button>
    <button
        class="btn"
        type="button"
        @click="filterHandler('mostViewers')"
        :class="[filterName === 'mostViewers' ? 'btn-primary' : 'btn-outline-primary']"
    >
      Eng ko'p ko'rilgan kinolar
    </button>
  </div>
</template>

<style scoped>

</style>