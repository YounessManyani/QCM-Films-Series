<template>
    <div class="question">
      <h3>{{ question.question }}</h3>
      <ul>
        <li v-for="(choice, index) in randomChoices" :key="choice">
          <Answer
            :for="`answer${index}`"
            :id="`answer${index}`"
            :disabled="hasAnswer"
            :value="choice"
            v-model="answer"
            :correctAnswer="question.correct_answer"
          />
        </li>
      </ul>
      <button :disabled="!hasAnswer" @click="emits('answer', answer)">
        Question Suivante
      </button>
    </div>
  </template>
  
  <script setup>
  import { computed, ref } from "vue";
  import {suffleArray} from '../functions/array.js'
  import Answer from "./Answer.vue";
  
  const props = defineProps({
    question: Object,
  });
  const answer = ref(null);
  const emits = defineEmits(["answer"]);
  
  const hasAnswer = computed(() => answer.value !== null);
  const randomChoices = computed(()=> suffleArray(props.question.choices))
  </script>
  
  <style>
  .question {
    padding-top: 2rem;
    display: table;
  }
  li {
    list-style: none;
    display: table;
  }
  .question button {
    margin-right: auto;
    display: block;
    background-color: brown;
    color: aliceblue;
  }
  </style>
  