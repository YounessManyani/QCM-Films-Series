<template>
    <h1>Recap</h1>
    <p>
        {{ hasWon ? quiz.success_message : quiz.failure_message }}
    </p>
    <p>
        Score : {{ score }}/ {{  quiz.questions.length  }}
    </p>
</template>

<script setup>
import { computed, defineProps } from 'vue';

const props = defineProps({
    quiz: Object,
    answers: Array
});

const score = computed(() => {
    let count = 0;
    props.quiz.questions.forEach((question, index) => {
        if (question.correct_answer === props.answers[index]) {
            count++;
        }
    });
   return count;
});
const hasWon = computed(()=> score.value >= props.quiz.minimum_score)
</script> 