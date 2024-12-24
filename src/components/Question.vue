<template>

    <div>
        <h3 >{{ question.question }}</h3>
        <ul>
            <li v-for="choice in question.choices" :key="choice">
                <Answer
                :id="`answer${index}`"
                :value="choice"
                v-model="answer"
                :correctAnswer="question.correct_answer"
                :disabled="hasAnswer"
                />
            </li>
        </ul>
        <button :disabled="!hasAnswer" @click="emits('answer' ,answer)">Question Suivante</button>
    </div>

</template>

<script setup>
import { computed, ref } from 'vue';
import Answer from './Answer.vue';

const props = defineProps({
    question : Object
})
const emits =defineEmits([`answer`])


const answer = ref(null)
const hasAnswer = computed(()=> answer.value !== null)
</script>

<style>

</style>