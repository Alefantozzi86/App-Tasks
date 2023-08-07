<template>
    <div>
    <Category
      v-for="category of data"
      :category="category"
      @click="$emit('selectCategory', category)"
      :key="category.id"
    />
</div>
  </template>
  
  <script>
  import Category from './Category.vue';
  
  export default {
    name: 'Categories',
    props: {
      data: Object,
    },
    components: {
      Category,
    },
  };
  </script>
  
  <script setup>
  defineProps(['data']);
  defineEmits(['selectCategory']);
  </script>
  
  <style></style>
  