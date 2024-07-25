<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script setup>

</script>

<style scoped>
.btn {
  align-self: flex-end;
  margin-top: 5px;
  padding: 10px 10px;
  background: #5e330e;
  border: 1px solid #0d0d0d;
  cursor: pointer;
  transition: 0.3s ease;
}
.btn:hover {
  background: #0d0d0d;
  border: 1px solid #5e330e;
  color: #fff;
}
</style>
