<template>
  <div>
    <button id="my-button" @click="$emit('back')">Back</button>
    <Task
      v-for="task of data"
      :data="task"
      :key="task.id"
      :categoryName="categoryName"
      @completeTask="(emitObject) => completeTask(emitObject)"
      @editTask="(emitObject) =>  editTask(emitObject)"
      @deleteTask="(emitObject) => deleteTask(emitObject, categories)"
    />
  </div>
</template>
<script>
import Task from "./Task.vue";
import { toRaw } from 'vue';
export default {
  name: "Tasks",
  props: {
    categoryName: String,
    data: Object,
    categories: Object
  },
  components: {
    Task,
  },
  emits: ['back', 'completeTask', 'editTask', 'deleteTask', 'updateCategories'],
  methods: {
    back() {
      this.$emit('back');
    },
    completeTask(task) {
      this.$emit('completeTask', task);
    },
    editTask(task) {
      this.$emit('editTask', task);
    },
    deleteTask(proxyTask, proxyCategories) {
      const task = toRaw(proxyTask);
      const rawCategories = toRaw(proxyCategories);
      const updatedCategories = rawCategories.map((category) => {
        if(category.name === task.categoryName) {
          const tasks = category.tasks.filter(categoryTask => categoryTask.id !== task.id);
          category.tasks = tasks;
          return category;
        } else {
          return category;
        }
      })
      this.$emit('updateCategories', updatedCategories);
    },
  },
};
</script>
<script setup>
defineProps(["data", "categoryName", "categories"]);
defineEmits(["back"]);
</script>
<style>
#my-button {
  padding: 12px 15px;
}
</style>