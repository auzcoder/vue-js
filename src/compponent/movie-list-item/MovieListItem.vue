<script setup>

import SearchPanel from "@/compponent/app/App.vue";
</script>

<template>
  <li class="list-group-item d-flex justify-content-between">
    <span class="list-group-item-label favourite">Poyitaxt - Sulton Abdulhamidxon</span>
    <input type="number" class="list-group-item-input" defaultValue="555" />
    <div class="d-flex justify-content-center align-items-center">
      <button class="btn-cookie btn-sm" type="button">
        <i class="fas fa-cookie"></i>
      </button>

      <button class="btn-trash btn-sm" type="button">
        <i class="fas fa-trash"></i>
      </button>
      <i class="fas fa-star like"></i>
    </div>
  </li>
<!--  <li>Sayrga chiqgan go'dak</li>-->
<!--  <li>Poyitaxt - Sulton Abdulhamidxon</li>-->
<!--  <li>Transformerlar - 2</li>-->
</template>

<style scoped>
.list-group-item {
  padding: 15px 20px;
  border-bottom: 1px solid #3d5a80;
}
.list-group-item:last-child {
  border-bottom: none;
}
.list-group-item span {
  line-height: 35px;
  font-size: 20px;
  cursor: pointer;
  width: 550px;
}

.list-group-item input {
  line-height: 35px;
  font-size: 20px;
  text-align: center;
  border: 0;
  outline: none;
}
.list-group-item button {
  width: 35px;
  height: 35px;
  margin: 3px;
  font-size: 17px;
  border: none;
  cursor: pointer;
}

.list-group-item .btn-cookie {
  color: #e09f3e;
}

.list-group-item .btn-trash {
  color: #e5383b;
}

.list-group-item .fa-star {
  width: 35px;
  height: 35px;
  text-align: center;
  line-height: 35px;
  font-size: 16px;
  color: #ffd700;
  transition: 0.3s all;
  transform: translate(30px);
  opacity: 0;
}

.list-group-item.like .fa-star {
  opacity: 1;
  transform: translate(0);
}

.list-group-item.favourite .list-group-item-label,
.list-group-item.favourite .list-group-item-input {
  color: #e09f3e;
}
</style>