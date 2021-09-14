<template>
  <div class="home">
    <ToDo></ToDo>
  </div>
</template>

<script>
// @ is an alias to /src
import ToDo from "@/components/ToDoForm.vue";

export default {
  components: {
    ToDo,
  },
};
</script>

<style>
body {
  background: linear-gradient(90deg, #e3ffe7 0%, #d9e7ff 100%);
  height: 100vh;
}
</style>
