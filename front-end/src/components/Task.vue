<template>
    <div class="task-wrapper">
      <div class="task-band"></div>
      <div class="task-body">
        <h2>Title</h2>
        <span>description</span>
      </div>
      <span>O</span>
      <span>📝</span>
      <span>X</span>
    </div>
  
  </template>
  
  <script>
  export default {
    name: 'Task',
    props: {
      task: Object,
    },
  };
  </script>
  
  <style>
  
  
  </style>