<template>
    <div>
    <button @click="$emit('back')">Back</button>
    <Task v-for="task of data" :data="task" :key="task.id" />
</div>
  </template>
  
  <script>
  import Task from './Task.vue';
  
  export default {
    name: 'Tasks',
    props: {
      data: Object,
    },
    components: {
      Task,
    },
  };
  </script>
  
  <script setup>
  defineProps(['data']);
  defineEmits(['back']);
  </script>
  
  <style>
button{
    font-family: "Inter", Sans-serif;
    font-size: 15px;
    font-weight: 100;
    background-color: #3B0A8A;
    border-radius: 800px 800px 800px 800px;
    padding: 10px 20px 10px 20px;
}
</style>
  