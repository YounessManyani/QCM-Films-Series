<template>
    <label :for="`answer${index}`" :class="classes">
      <input
        :id="id"
        type="radio"
        name="answer"
        v-model="model"
        :value="value"
        :disabled="disabled"
        
      />
      {{ value }}
    </label>
  </template>
  
  <script setup>
  import { computed } from 'vue';
  
  
  const props = defineProps({
      id:String,
      disabled:Boolean,
      value:String,
      correctAnswer:String
  })
  const model = defineModel()
  const classes = computed(()=>({
      disabled:props.disabled,
      right: props.disabled && props.value === props.correctAnswer,
      wrong: props.disabled && props.value !== props.correctAnswer && model.value === props.value
  }))
  </script>
  <style>
  .disabled{
      opacity: .5;
  }
  .right{
      color: green;
  }
  .wrong{
      color: red
  }
  </style>
  