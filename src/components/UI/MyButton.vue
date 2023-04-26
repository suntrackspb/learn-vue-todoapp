<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "MyButton"
}
</script>

<style scoped>
.btn {
  padding: 5px 20px;
  background: none;
  color: blueviolet;
  font-size: 20px;
  border: 1px solid blueviolet;
  border-radius: 5px;
}
.btn:hover {
  color: white;
  background: blueviolet;
  border: 1px solid white;
}
</style>