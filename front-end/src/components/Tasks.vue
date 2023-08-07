<template>
    <div>
    <button id="my-button" @click="$emit('back')">Back</button>
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

#my-button{
    padding: 12px 15px
}
</style>
  