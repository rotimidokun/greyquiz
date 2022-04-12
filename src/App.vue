<script setup lang="ts">
import QuizCard from "./components/QuizCard.vue";
</script>

<template>
  <div class="container">
    <QuizCard />
  </div>
</template>

<style scoped>
.container {
  background: #0F2027;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right, #2C5364, #203A43, #0F2027);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right, #2C5364, #203A43, #0F2027); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */


  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
