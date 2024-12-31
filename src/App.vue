<template>
  <div class="container">
    <div v-if="state === 'error'">
      <p>Impossible de carger le quiz</p>
    </div>
    <div :aria-busy="state === 'loading'">
      <div v-if="state === 'loading'" class="loader"></div>
      <div v-else>
        <Quiz :quiz="quiz" v-if="quiz" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import Quiz from "./components/Quiz.vue";

const quiz = ref(null);
const state = ref("loading");

onMounted(() => {
  fetch("/quiz.json")
    .then((r) => {
      if (r.ok) {
        return r.json();
      }
      throw new Error("Impossible de lire le json ");
    })
    .then((data) => {
      quiz.value = data;
      state.value = "idle";
    })
    .catche((e) => {
      state.value = "error";
    });
});
</script>
<style>
.container {
  margin-top: 2rem;
}
.loader {
  border: 5px solid #f3f3f3; 
  border-top: 5px solid #3498db; 
  border-radius: 50%; 
  width: 40px; 
  height: 40px; 
  animation: spin 2s linear infinite; 
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
