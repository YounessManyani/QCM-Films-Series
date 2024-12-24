<template>
    <label for="id" :class="classes" >
                    <input id ="id" type="radio" name="answer"
                    v-model="model" :value="value" :disabled="disabled"
                    >
                    {{ value }}
    </label>
</template>

<script setup>
import { computed } from 'vue';


const props = defineProps ({
    id : String,
    value: String,
    correctAnswer:String,
    disabled: Boolean
})
const model = defineModel()
const classes = computed (()=>({
    right : props.disabled && props.value === props.correctAnswer,
    wrong : props.disabled && props.value !== props.correctAnswer && model.value === props.value
}))

</script>
<style>
.right{
    color: green;
}
.wrong{
    color: red;
}
</style>