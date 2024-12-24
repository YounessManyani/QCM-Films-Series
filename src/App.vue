<template>
  <div id="app">
    <Quiz :quiz="quizData" v-if="quizData"/>
  </div>
</template>

<script lang="ts" setup>
import { onMounted, ref } from 'vue';
import Quiz from './components/Quiz.vue';
const quizData = ref(null);

onMounted(() => {
  fetch('/quiz.json')
    .then(response => {
      if (!response.ok) throw new Error('Failed to load the quiz data');
      return response.json();
    })
    .then(data => {
      quizData.value = data;
    })
    .catch(error => console.error('Error:', error));
});
</script>

<style>

</style>
