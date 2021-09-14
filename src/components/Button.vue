<template>
  <div>
      <slot></slot>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
button {
  width: 4rem;
  height: 2.1rem;
  border: none;
  border-radius: 0 0.3rem 0.3rem 0;
  background-color: #f8f8f8bd;
  cursor: pointer;
}

button:hover {
  filter: brightness(1.5);
  transition: 0.4s;
}
</style>