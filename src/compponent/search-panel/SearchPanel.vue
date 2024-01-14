<script setup>
export default {
  props: {
    updateTermHandler: {
      type: Function,
      required: true,
    },
  },
}
</script>

<template>
  <input type="text" class="form-control search-panel" placeholder="Kinolarni qidirish..." />
</template>

<style scoped>
.search-panel {
  margin-bottom: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>